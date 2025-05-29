`srgcd(a::Pol,b::Pol)`

部分結果 gcd: 一意因子分解環上の多項式の gcd

```julia-repl
julia> srgcd(4q+4,6q^2-6)
Pol{Int64}: 2q+2
```

Knuth AOCP2 4.6.1 アルゴリズム C を参照してください。
