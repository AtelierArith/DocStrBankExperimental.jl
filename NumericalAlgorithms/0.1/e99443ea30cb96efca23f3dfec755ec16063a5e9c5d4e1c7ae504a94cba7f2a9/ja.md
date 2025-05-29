```
FindRoot1D(f::Function, p0::Float64, p1::Float64, NMAX::UInt64, tol::Float64)
```

関数の一次元根を割線法で計算します。割線法は次の差分方程式で定義されます：

$$
x_{n}=x_{n-1}-f(x_{n-1}){\frac {x_{n-1}-x_{n-2)){f(x_{n-1})-f(x_{n-2})))={\frac {x_{n-2}f(x_{n-1})-x_{n-1}f(x_{n-2})}{f(x_{n-1})-f(x_{n-2})))
$$
