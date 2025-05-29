```
root(a::T, n::Int; check::Bool=true) where T <: Integer
```

$$
a
$$

の$n$-乗根を返します。`check=true`の場合、関数は入力が完全な$n$-乗であるかどうかをテストします。それ以外の場合は例外が発生します。$n > 0$である必要があります。
