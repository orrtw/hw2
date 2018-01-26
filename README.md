
# Отчет по работе 
## Журбина Наталия
>**№1**
x(max)=01111111011111111111111111111111
x(10)=3.4*10^38

> **№2**
x(min)=00000000000000000000000000000001
x(10)=3.4*10^-45

> №3
```html
<under =1 
over = 1 
N=100 
eps=1.0 
for i in range (N) : 
    under = under/2 
    over=over*2 
    print ('over =',over,', under =', under)>
```

>  **over = 1267650600228229401496703205376 , under = 7.888609052210118e-31**

![screenshot of sample](https://pp.userapi.com/c831109/v831109606/5e576/TG9STKqiFu4.jpg)

> №4 
```html
<N=100 
eps=1.0 
for i in range (N) : 
  eps = eps /2 
  one_Plus_eps =1.0 +eps 
  print ('eps =',eps,', one + eps =', one_Plus_eps)>
```

> eps= 2.220446049250313e-16 , one + eps = 1.0000000000000002
![screenshot of sample](https://pp.userapi.com/c840621/v840621606/4aba1/VfcjlknBpnY.jpg)

> №5
```html
<N=100 
eps=complex(1, 1) 
for i in range (N) : 
	eps = eps /2 
	one_Plus_eps =complex( 1, 1)+eps 
	print ('eps =',eps,', one + eps =', one_Plus_eps)
>
```

> eps = (2.220446049250313e-16+2.220446049250313e-16j) , one + eps = (1.0000000000000002+1.0000000000000002j)
![screenshot of sample](https://pp.userapi.com/c841325/v841325606/58178/uSgyAP_gDTU.jpg)

> №6

```html
<import math
x=math.pi/2
eps=10**(-5) 
s=x 
t=x 
i=2 
while abs(t/s)>eps: 
	t=(-x**2/((2*i-1)*(2*i-2)))*t 
	s=s+t 
	i=i+1 
import math
a=math.fabs(s-math.sin(x))/math.sin(x)
print ('s=',s, 'tmax=',t, 'a=',a, 'i=', i)
>
```
![screenshot of sample](https://pp.userapi.com/c830309/v830309599/5c47f/TGcNxy_BYMw.jpg)

| sum   | t max             | ошибка | степень eps |
| ------------- |:------------------:| -----:| -----:|
| 0.9999999999939768    | -6.688035109811466e-106.023181953196399e-12    |  6.023181953196399e-12 | -8 |
| 1.0000000000000437    | 6.066935731106194e-12 |   4.374278717023117e-14 | -10|
| 1.0000000000000002 | 3.4140529700331598e-31    |   2.220446049250313e-16 | -30|
|1.0000000000000002 | 6.382145039734999e-51 | 2.220446049250313e-16 | -50|

- Из данной таблицы мы видим, что при достаточно малых значениях х алгоритм сходится к 1, 
 Значение тем ближе к 0, чем меньше  точность.
- После того, как наша точность превысила машинную, значение суммы ряда остается постоянным( при х=pi/2 =1.0000000000000002)
- Без использования формулы приведения ( sin(x+2*n*pi)=sin(x)) существует диапазон х, для которых алгоритм сходится, но не к 0, а к 1. Что видно из данной таблицы.


| sum      | делитель pi (pi/k)  | 
| ------------- |:--------------:| 
| 0.9980267284282714    | 50  | 
| 0.9995065603657319  | 100 |   
| 0.9999950652018581  | 1000  |

- Приприменении формул приведения алгоритм также сходится при малым х.
 

-  "Плохая" версия алгоритма
```html
<import math
x=math.pi*2
eps=10**(-50) 
s=x 
t=x 
i=2 
while abs(t/s)>eps: 
	import math
	t=(-1)**(i-1)*(x**(2*i-1))/math.factorial((2*i-1))*t 
	s=s+t 
	i=i+1 
import math
a=math.fabs(s-math.sin(x))/math.sin(x)
print ('s=',s, 'tmax=',t, 'a=',a, 'i=', i)
>
```
| "Хороший"       | "Плохой"                | 
| ------------- |:------------------:| 
| 0.019757158783946512     | 0.019758418960677735    | 
| 0.15643446504023087     | 0.1569781647954669 |   
| 4.3878919606925197e-16  | -1782193851.3401673        |   

![screenshot of sample](https://pp.userapi.com/c841620/v841620599/603a8/ckUbyODGDmU.jpg)

-  Из данного графика мы видим, что при больших точностях функция ошибок от количества слагаемых выходит на константу

> №7
```html
<import math
import sys

a= float(input("a = "))
if a == 0:
	print ('не является квадратным')
	sys.exit()
	
b = float(input("b = "))
c = float(input("c = "))

D = b**2- 4*a*c
if D == 0:
	m=-b/2*a
	print ('x =', m) 
	sys.exit()
if D > 0: 
	n=(-b + math.sqrt(D))/ 2*a
	m=(-b - math.sqrt(D))/ 2*a
	print ('x1 =',n,'x2 =',m)
else:
	D<0
	D=complex(D**0.5)
	n=(-b+complex((D**0.5)))/2*a
	m=(-b-complex((D**0.5)))/2*a
	print ('x1 =',n,'x2 =',m)
    
>
```

![screenshot of sample](https://pp.userapi.com/c840322/v840322599/240cc/6wb2_sZ4Bf0.jpg)

