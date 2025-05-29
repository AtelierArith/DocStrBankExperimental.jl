```
is_power(a::T, n::Int) where T <: Integer
```

Return `true, q` if $a$ is a perfect $n$-th power with $a = q^n$. Otherwise return `false, 0`. We require $n > 0$.
