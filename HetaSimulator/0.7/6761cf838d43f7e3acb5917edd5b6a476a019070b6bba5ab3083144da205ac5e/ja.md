```
struct Model{IF,OF,EV,SG,EA, MM} <: AbstractModel
  init_func::IF
  ode_func::OF
  events::EV
  saving_generator::SG
  records_output::AbstractVector{Pair{Symbol,Bool}}
  constants::NamedTuple
  events_active::EA
  mass_matrix::MM
end
```

ODEモデルのコアプロパティを格納する構造体。これはHetaプラットフォームの1つの名前空間の内容を表します。

モデルの内容のリストを取得するには、次のメソッドを使用します: constants(model), records(model), switchers(model)。

デフォルトのモデルオプションを取得するには、次のメソッドを使用します:  `events_active(model)`, `events_save(model)`, `observables(model)`。これらの値は[`Scenario`]{@ref}によって上書きすることができます。
