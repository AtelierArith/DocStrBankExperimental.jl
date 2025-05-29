```
swinnerton_dyer(V::Vector, x::Generic.Poly{<:Generic.RationalFunctionFieldElem})
swinnerton_dyer(n::Int, x::Generic.Poly{<:Generic.RationalFunctionFieldElem})
```

Compute the minimal polynomial of $\sum \pm \sqrt{t+v_i}$ evaluated at $x$. $t$ is the generator of the base field of the parent of $x$.

In the second variant, the polynomial has roots $\sum\pm\sqrt{t+i}$ for   $i=1,\ldots,n$.
