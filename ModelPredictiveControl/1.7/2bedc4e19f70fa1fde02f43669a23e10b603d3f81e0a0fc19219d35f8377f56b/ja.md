```
initstate!(model::SimModel, u, d=[]) -> x
```

`model.x0`を操作された入力`u`と測定された摂動`d`の定常状態で初期化します。

このメソッドは、定常状態でモデルの状態$\mathbf{x}$を初期化しようとします。`u`と`d`の運転点を削除し、[`steadystate!`](@ref)を呼び出します：

  * `model`が[`LinModel`](@ref)の場合、このメソッドは現在の入力`u`と測定された摂動`d`の定常状態を計算します。
  * それ以外の場合、`model.x0`は変更されません。手動で変更するには[`setstate!`](@ref)を使用してください。

# 例

```jldoctest
julia> model = LinModel(tf(6, [10, 1]), 2.0);

julia> u = [1]; x = initstate!(model, u); y = round.(evaloutput(model), digits=3)
1-element Vector{Float64}:
 6.0
 
julia> x ≈ updatestate!(model, u)
true
```
