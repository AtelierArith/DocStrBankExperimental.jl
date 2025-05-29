```
factor(n::Integer) -> Primes.Factorization
```

整数 `n` の素因数分解を計算します。返されるオブジェクトは `Factorization` 型で、キーは因数に対応し、ソートされた順序で格納されます。各キーに関連付けられた値は、その因数が因数分解に現れる回数（すなわち重複度）を示します。

```julia
julia> factor(100)
2^2 ⋅ 5^2
```

便利のために、負の数 `n` は `-1*(-n)` として因数分解されます（すなわち `-1` は因数と見なされます）、また `0` は `0^1` として因数分解されます：

```julia
julia> factor(-9)
-1 ⋅ 3^2

julia> factor(0)
0

julia> collect(factor(0))
1-element Array{Pair{Int64,Int64},1}:
 0=>1
```
