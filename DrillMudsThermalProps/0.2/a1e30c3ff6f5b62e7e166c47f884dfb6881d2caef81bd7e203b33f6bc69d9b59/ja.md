```
TestFluid <: Fluid
```

パッケージ内で新しい流体を定義するために必要なすべての最小パラメータを持つテンプレート流体として定義された型。この流体を使用したすべてのプロパティに対して、未実装のプロパティのために関数呼び出しはエラーをスローする必要があります。

# パラメータ

  * `name::Symbol`: 流体の名前。デフォルト値: `:TestFluid`。
  * `ρ::Float64`: 標準条件下での流体の密度 [kg/m³]。デフォルト値: `1000.0`。
  * `cₚ::Float64`: 標準条件下での流体の比熱 [J/kg K]。デフォルト値: `4000.0`。
  * `μ::Flaot64`: 標準条件下での流体の動的粘度 [Pa s]。デフォルト値: `1.002E-3`。
  * `k::Float64`: 標準条件下での流体の熱伝導率 [W/m K]。デフォルト値: `0.58`。
