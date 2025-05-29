```
HydroBucket{N,S} <: AbstractBucket
```

モデルコンポーネントを整理し実行するための柔軟な構造体です。

# フィールド

  * `fluxes::Vector{<:AbstractHydroFlux}`: 適用されるプロセス関数のリスト。
  * `dfluxes::Vector{<:AbstractStateFlux}`: ODEサポートのための状態導関数のリスト。
  * `flux_funcs::Vector{<:Function}`: すべてのフラックスを効率的に評価するための事前コンパイルされた関数。
  * `ode_funcs::Union{Nothing,Vector}`: ODE計算のための関数、または必要ない場合は`nothing`。
  * `infos::NamedTuple`: 入力、出力、状態、パラメータ、ニューラルネットワークの名前を含むメタデータ。

# コンストラクタ

```julia
HydroBucket(; name=nothing, fluxes, dfluxes=StateFlux[])
```

  * `name::Union{Symbol,Nothing}`: バケットのオプション識別子。自動生成された名前がデフォルトです。
  * `fluxes::Vector{<:AbstractHydroFlux}`: 必須。主な計算要素。
  * `dfluxes::Vector{<:AbstractStateFlux}`: オプション。ODEサポートのための状態導関数。

# 使用例

```julia
bucket = HydroBucket(
    name = :example_bucket,
    fluxes = [MyFlux1(), MyFlux2()],
    dfluxes = [MyStateFlux()]
)
```

# 注意事項

  * 型パラメータ `N` と `S` は内部で設定され、一般的にユーザーが指定するものではありません。
  * より大きなモデリングシステムでのモジュール性と統合のために設計されています。
  * 効率的な関数生成とメタデータ追跡は自動的に処理されます。
