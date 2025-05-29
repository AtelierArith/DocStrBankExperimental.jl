```
root(x::QQFieldElem, n::Int; check::Bool=true)
```

Return the $n$-the root of $x$. We require $n > 0$ and that $x \geq 0$ if $n$ is even. By default the function tests whether the input was a perfect $n$-th power and if not raises an exception. If `check=false` this check is omitted.
