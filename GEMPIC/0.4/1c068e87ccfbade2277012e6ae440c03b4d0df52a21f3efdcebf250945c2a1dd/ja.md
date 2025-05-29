```
sample!(d, pg)
```

1D2V空間におけるランドー減衰を初期化するための確率分布からのサンプリング。

$$
f_0(x,v,t) = \frac{n_0}{2π v_{th}^2} ( 1 + \alpha cos(k_x x))
 exp( - \frac{v_x^2+v_y^2}{2 v_{th}^2})
$$

ニュートン関数は、ニュートン法を用いて方程式 $P(x)-r=0$ を解きます。

$$
x^{n+1} = x^n – (P(x)-(2\pi r / k)/f(x) 
$$

ここで 

$$
P(x) = \int_0^x (1 + \alpha cos(k_x y)) dy = x + \frac{\alpha}{k_x} sin(k_x x)
$$
