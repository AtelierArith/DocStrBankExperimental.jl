```
sample!(d, pg)
```

Sampling from a probability distribution to initialize a Landau damping in 1D2V space.

$$
f_0(x,v,t) = \frac{n_0}{2π v_{th}^2} ( 1 + \alpha cos(k_x x))
 exp( - \frac{v_x^2+v_y^2}{2 v_{th}^2})
$$

The newton function solves the equation $P(x)-r=0$ with Newton’s method

$$
x^{n+1} = x^n – (P(x)-(2\pi r / k)/f(x) 
$$

with 

$$
P(x) = \int_0^x (1 + \alpha cos(k_x y)) dy = x + \frac{\alpha}{k_x} sin(k_x x)
$$
