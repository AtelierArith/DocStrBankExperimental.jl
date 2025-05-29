```julia
mutable struct Simulation{MD, CK}
```

`model`のシミュレーションのための`Simulation`オブジェクトを構築します。`Simulation`オブジェクトは、`model`のシミュレーションの状態を監視するために使用されます。`simdir`は、シミュレーションファイル（ログ、データファイルなど）が記録されるディレクトリのパスです。`simname`は`Simulation`の名前であり、`simprefix`は`Simulation`の名前のプレフィックスです。`logger`は、`model`のシミュレーションステップを記録するために使用されます。詳細については、[`Model`](@ref)、[`Logging`](https://docs.julialang.org/en/v1/stdlib/Logging/)を参照してください。

# フィールド

  * `model::Any`: シミュレーションされるモデル
  * `clock::Any`: シミュレーションクロック
  * `path::String`: シミュレーションファイルが記録されるパス
  * `logger::Union{Base.CoreLogging.ConsoleLogger, Base.CoreLogging.SimpleLogger}`: シミュレーションロガー
  * `state::Symbol`: シミュレーション状態
  * `retcode::Symbol`: シミュレーション戻りコード
  * `name::String`: シミュレーション名
