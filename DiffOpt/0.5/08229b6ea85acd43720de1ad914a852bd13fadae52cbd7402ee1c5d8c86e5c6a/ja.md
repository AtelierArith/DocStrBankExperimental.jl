```
diff_optimizer(optimizer_constructor)
```

`DiffOpt.Optimizer`を作成します。これは内部最適化器とその他のユーティリティメソッドを持つMOIレイヤーです。結果（プライマル、デュアル、スラック値）は、`optimizer_constructor`を使用してインスタンス化された内部最適化器をクエリすることによって取得されます。これらの値は、問題データに関するヤコビアンを見つけるために必要です。

任意のソルバーを使用して微分可能なモデルを定義します。例：

```julia
julia> import DiffOpt, HiGHS

julia> model = DiffOpt.diff_optimizer(HiGHS.Optimizer)
julia> set_attribute(model, DiffOpt.ModelConstructor, DiffOpt.QuadraticProgram.Model) # 微分手法のオプション選択
julia> x = model.add_variable(model)
julia> model.add_constraint(model, ...)
```
