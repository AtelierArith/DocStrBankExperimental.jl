```
order(f, w)
```

Compute the order $(v_1, v_2)$ of the given complements.

The $j$-th order of $f$ at $w=(w_1,w_2)$ can be computed by the number of zeros (minus the number of poles) of the one-variable Laurent-polynomial

$$
    u ↦ f(c_1^u^{δ_{1j}}, c_2^u^{δ_{2j}})
$$

inside the unit circle $|u|=1$, where $(c1, c2)$ is any vector with $Log(c1, c2) = w$ [^1].

In order to compute this we can use the [argument principle](https://en.m.wikipedia.org/wiki/Argument_principle). For this we have to rewrite the integral (here only for the first component of the order)

$$
rac{1}{2πi}∫_{|u|=1}rac{f'(e^{w_1}u, e^{w_2})}{f(e^{w_1}u, e^{w_2})}du
$$

With a change of variables we get

$$
rac{1}{2πi}∫_0^{2π}rac{f'(e^{w_1}e^{iθ}, e^{w_2})}{f(e^{w_1}e^{iθ}, e^{w_2})}ie^{iθ}dθ
$$

[^1]: Forsberg, Mikael, Mikael Passare, and August Tsikh. "Laurent determinants and arrangements of hyperplane PolynomialAmoebas." Advances in mathematics 151.1 (2000): 45-70.
