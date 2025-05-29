```
interpolate(basis::BSplineBasis, xvalues, yvalues; indices=eachindex(basis)) -> Spline
```

Bスプライン基底 `basis` における `xvalues` と `yvalues` によって与えられたデータを補間します。`indices` が指定されている場合、`basis` の指定されたインデックスの基底関数のみが使用されます。

スプライン補間は、行列 `B = [basis[i](x) for x=xvalues, i=indices]` を作成し、その後 `B\yvalues` を計算することによって行われます。

参照: [`approximate`](@ref)

# 例

```jldoctest
julia> basis = BSplineBasis(5, 1:10);

julia> xs = range(1, stop=10, length=length(basis)); ys = log.(xs);

julia> spl = interpolate(basis, xs, ys)
BSplines.Spline{BSplines.BSplineBasis{UnitRange{Int64}}, Vector{Float64}}:
 basis: 13-element BSplineBasis{UnitRange{Int64}}:
  order: 5
  breakpoints: 1:10
 coeffs: [0.0, 0.248019, 0.596872, 0.946671, 1.26894, 1.51405, 1.71149, 1.87666, 2.01856, 2.14292, 2.22592, 2.27758, 2.30259]

julia> spl(float(ℯ))
0.9999766059171411
```
