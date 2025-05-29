```
root(a::T, n::Int; check::Bool=true) where T <: Integer
```

Return the $n$-th root of $a$. If `check=true` the function will test if the input was a perfect $n$-th power, otherwise an exception will be raised. We require $n > 0$.
