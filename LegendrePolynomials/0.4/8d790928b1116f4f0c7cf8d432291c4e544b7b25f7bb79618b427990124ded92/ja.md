```
collectdnPl!(v::AbstractVector, x; lmax::Integer, n::Integer)
```

引数 `x` に対するレジェンドル多項式 $P_\ell(x)$ の $n$ 番目の導関数を計算し、すべての次数 `l = 0:lmax` の結果を `v` に格納します。

導関数の次数 `n` はゼロ以上でなければなりません。

出力では、`v[l + firstindex(v)] == dnPl(x, l, n)` が成り立ちます（`l = 0:lmax` の場合）。

# 例

```jldoctest
julia> v = zeros(4);

julia> collectdnPl!(v, 0.5, lmax = 3, n = 2)
4-element Vector{Float64}:
 0.0
 0.0
 3.0
 7.5
```
