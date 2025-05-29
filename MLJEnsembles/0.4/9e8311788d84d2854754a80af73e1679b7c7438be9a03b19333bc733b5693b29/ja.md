```
EnsembleModel(model,
              atomic_weights=Float64[],
              bagging_fraction=0.8,
              n=100,
              rng=GLOBAL_RNG,
              acceleration=CPU1(),
              out_of_bag_measure=[])
```

`n` 個の `model` のクローンのアンサンブルをトレーニングするためのモデルを作成します。オプションのバギングがあります。アンサンブリングは、`fit!(machine(atom, data...))` が繰り返し呼び出したときに同一のモデルを作成しない場合（すなわち、ノード選択基準がランダム化された決定木のような確率的モデル）、または `bagging_fraction` が 1.0 未満に設定されている場合、またはその両方の場合に有用です。

ここでの原子 `model` は、`AbstractVector{<:Finite}`（単一ターゲット分類器）または `AbstractVector{<:Continuous}`（単一ターゲット回帰器）を持つターゲットをサポートする必要があります。

`rng` が整数の場合、`MersenneTwister(rng)` がバギングに使用される乱数生成器です。それ以外の場合は、`AbstractRNG` オブジェクトが期待されます。

原子予測は、ベクトル `atomic_weights` に従ってオプションで重み付けされます（外部最適化を可能にするため）。ただし、`model` が `Deterministic` 分類器である場合は、`atomic_weights` は無視されます。

アンサンブルモデルは、`atom` の対応するスーパタイプに応じて `Deterministic` または `Probabilistic` です。決定論的分類器の場合（`target_scitype(atom) <: Abstract{<:Finite}`）、予測は多数決であり、回帰器の場合（`target_scitype(atom)<: AbstractVector{<:Continuous}`）は通常の平均です。確率的予測は、原子確率分布/質量関数を平均することによって得られます。特に、回帰器の場合、各入力パターンに対するアンサンブル予測は、Distributions.jl パッケージの `MixtureModel{VF,VS,D}` 型を持ち、ここで `D` は `atom` の予測分布の型です。

分散コンピューティングには `acceleration=CPUProcesses()` を指定し、マルチスレッドには `CPUThreads()` を指定します。

`out_of_bag_measure` によって単一の測定または非空の測定ベクトルが指定されている場合、バギング外のパフォーマンスの推定値がトレーニングレポートに書き込まれます（アンサンブルモデルをラップしたトレーニング済みマシンで `report` を呼び出します）。

*重要:* アンサンブルモデルのためのマシンを構築する際に、観測ごとの重みまたはクラス重み `w`（原子重みと混同しないでください）が指定されている場合、`mach = machine(ensemble_model, X, y, w)` のように、`w` はそれをサポートする `out_of_bag_measure` に指定された任意の測定で使用されます。
