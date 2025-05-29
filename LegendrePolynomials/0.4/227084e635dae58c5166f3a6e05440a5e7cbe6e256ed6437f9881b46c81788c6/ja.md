```
collectPl!(v::AbstractVector, x; [lmin::Integer = 0], [lmax::Integer = length(v) - 1 + lmin], [kwargs...])
```

引数 `x` と次数 `l = lmin:lmax` に対してレジェンドル多項式 $P_\ell(x)$ を計算し、`v` に格納します。

出力では `v[firstindex(v) + l] == Pl(x, l; kwargs...)` となります。

# オプションのキーワード引数

  * `norm`: 関数で使用される正規化。可能なオプションは `Val(:standard)`（デフォルト）と `Val(:normalized)` です。`norm = Val(:normalized)` の場合に得られる関数は L2 ノルムが $1$ になります。

# 例

```jldoctest
julia> v = zeros(4);

julia> collectPl!(v, 0.5);

julia> all(zip(0:3, v)) do (l, vl); vl ≈ Pl(0.5, l); end
true

julia> collectPl!(v, 0.5, norm = Val(:normalized));

julia> all(zip(0:3, v)) do (l,vl); vl ≈ Pl(0.5, l, norm = Val(:normalized)); end
true

julia> v = zeros(0:4);

julia> collectPl!(v, 0.5, lmax = 3) # l は 0 から 3 までのみが populated されます
5-element OffsetArray(::Vector{Float64}, 0:4) with eltype Float64 with indices 0:4:
  1.0
  0.5
 -0.125
 -0.4375
  0.0
```
