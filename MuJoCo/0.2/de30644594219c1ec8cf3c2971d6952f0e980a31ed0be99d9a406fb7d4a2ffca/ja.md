```
show_docs(obj, field::Symbol)
```

`obj`の`field`（`obj.field`のように）のドキュメントをコンソールに表示します。

インスタンスが利用できない場合は、`obj`を型として指定することもできます。

# 使用例

直接型を使用した場合:

```julia
julia> show_docs(Model, :nv)
Model.nv: 自由度の数 = dim(qvel)
```

インスタンスを使用した場合:

```julia
julia> model, data = MuJoCo.sample_model_and_data();
julia> show_docs(model, :nq)
Model.nq: 一般化座標の数 = dim(qpos)
julia> show_docs(data, :qvel)
Data.qvel: 速度 (nv x 1)
```
