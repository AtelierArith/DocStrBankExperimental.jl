```
iroot(a::T, n::Int) where T <: Integer
```

Return the truncated integer part of the $n$-th root of $a$ (round towards zero). We require $n > 0$ and also $a \geq 0$ if $n$ is even.
