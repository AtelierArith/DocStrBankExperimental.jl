```
linearize!(linmodel::LinModel, model::SimModel; <keyword arguments>) -> linmodel
```

`model`を線形化し、その結果を`linmodel`に格納します（インプレース）。

キーワード引数は[`linearize`](@ref)と同じです。`model`のシミュレーションがメモリを割り当てない場合、コードはメモリ割り当てなしで実行されます。

# 例

```jldoctest
julia> model = NonLinModel((x,u,_,_)->x.^3 + u, (x,_,_)->x, 0.1, 1, 1, 1, solver=nothing);

julia> linmodel = linearize(model, x=[10.0], u=[0.0]); linmodel.A
1×1 Matrix{Float64}:
 300.0

julia> linearize!(linmodel, model, x=[20.0], u=[0.0]); linmodel.A
1×1 Matrix{Float64}:
 1200.0
```
