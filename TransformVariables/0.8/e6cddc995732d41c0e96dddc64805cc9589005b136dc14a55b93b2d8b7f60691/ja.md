```julia
domain_label(transformation, index)

```

座標を識別するために使用できる文字列を返します。主にデバッグやグラフおよびデータサマリーの生成に使用されます。

変換はヒューリスティックラベルを提供する場合があります。

変換は `_domain_label` を実装する必要があります。

# 例

```jldoctest
julia> t = as((a = asℝ₊,
            b = as(Array, asℝ₋, 1, 1),
            c = corr_cholesky_factor(2)));

julia> [domain_label(t, i) for i in 1:dimension(t)]
3-element Vector{String}:
 ".a"
 ".b[1,1]"
 ".c[1]"
```
