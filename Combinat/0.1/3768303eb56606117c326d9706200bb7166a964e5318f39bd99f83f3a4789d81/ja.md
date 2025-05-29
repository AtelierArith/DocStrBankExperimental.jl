`moebius(n::Integer)`

古典的なメビウス関数は、整数の順序集合における可除性のメビウス関数です。平方フリー整数の外ではゼロであり、平方フリー整数に対しては `(-1)ⁿ` で、ここで n は素因子の数です。

```julia-repl
julia> moebius.(1:6)
6-element Vector{Int64}:
  1
 -1
 -1
  0
 -1
  1
```
