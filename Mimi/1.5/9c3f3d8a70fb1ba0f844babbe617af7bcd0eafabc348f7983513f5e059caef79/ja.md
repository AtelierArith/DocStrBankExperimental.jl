```
create_marginal_model(base::Model, delta::Float64=1.0)
```

`base`がベースラインモデルであり、`delta`が`marginal`モデルを作成するために使用される差である`MarginalModel`を作成します。内部の`ModelDef`を`base`と`marginal`の間で共有する結果の`MarginaModel`を返します。
