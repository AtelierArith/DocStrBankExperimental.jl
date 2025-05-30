```
default_nint(model::LinModel, i_ym=1:model.ny, nint_u=0) -> nint_ym
```

測定出力ごとのデフォルトの積分器量 `nint_ym` を取得します [`LinModel`](@ref) のために。

引数 `i_ym` と `nint_u` は、それぞれ測定出力のインデックスと各操作入力における積分器量です。デフォルトでは、各測定出力に1つの積分器が追加されます。もし拡張モデルの $\mathbf{Â, Ĉ}$ 行列が観測不可能になると、積分器は削除されます。このアプローチは、安定した、積分する、そして不安定な `model` に対してうまく機能します（例を参照）。

# 例

```jldoctest
julia> model = LinModel(append(tf(3, [10, 1]), tf(2, [1, 0]), tf(4,[-5, 1])), 1.0);

julia> nint_ym = default_nint(model)
3-element Vector{Int64}:
 1
 0
 1
```
