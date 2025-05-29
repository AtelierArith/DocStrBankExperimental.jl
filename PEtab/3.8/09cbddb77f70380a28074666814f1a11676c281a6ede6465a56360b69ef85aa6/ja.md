```
PEtabModel(sys, observables::Dict{String, PEtabObservable}, measurements::DataFrame,
           parameters::Vector{PEtabParameter}; kwargs...)
```

`ReactionSystem` または `ODESystem` モデルから、モデルを `measurements` にリンクする `observables` と推定する `parameters` を作成し、パラメータ推定のための `PEtabModel` を作成します。

`PEtabModel` の作成方法の例については、ドキュメントを参照してください。

また、[`PEtabObservable`](@ref)、[`PEtabParameter`](@ref)、および [`PEtabEvent`](@ref) も参照してください。

## キーワード引数

  * `simulation_conditions = nothing`: 各シミュレーション条件の初期種の値および/またはモデルパラメータを指定するオプションの辞書。モデルに複数のシミュレーション条件がある場合にのみ必要です。
  * `events = nothing`: `PEtabEvent` として提供されるオプションのモデルイベント（コールバック）。複数のイベントは `Vector` の `PEtabEvent` として提供する必要があります。
  * `verbose::Bool = false`: `PEtabModel` を構築する際に進行状況を印刷するかどうか。

```
PEtabModel(path_yaml; kwargs...)
```

`path_yaml` にあるYAMLファイルの標準形式でPEtab問題をインポートし、パラメータ推定のための `PEtabModel` にします。

PEtab問題のインポート方法の例については、ドキュメントを参照してください。

## キーワード引数

  * `ifelse_to_callback::Bool = true`: `ifelse` (SBMLの区分的) 表現を [コールバック](https://github.com/SciML/DiffEqCallbacks.jl) に書き換えるかどうか。この設定によりシミュレーションの実行時間が改善されます。これを `true` に設定することを強く推奨します。
  * `verbose::Bool = false`: `PEtabModel` を構築する際に進行状況を印刷するかどうか。
  * `write_to_file::Bool = false`: 生成されたJulia関数をPEtab問題と同じディレクトリにファイルとして書き込むかどうか。デバッグに便利です。
