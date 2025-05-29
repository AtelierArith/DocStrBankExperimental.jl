```
Model(optimizer_factory; add_bridges::Bool = true)
```

提供されたオプティマイザとブリッジ設定で新しいJuMPモデルを返します。

`optimizer_factory`および`add_bridges`引数の説明については、[`set_optimizer`](@ref)を参照してください。

## 例

オプティマイザを`Ipopt`に設定したモデルを作成します：

```julia
model = Model(Ipopt.Optimizer)
```

匿名関数を渡して`Gurobi.Optimizer`を作成し、ブリッジを無効にします：

```julia
env = Gurobi.Env()
model = Model(() -> Gurobi.Optimizer(env); add_bridges = false)
```
