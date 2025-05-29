```
BinaryThresholdPredictor(model; threshold=0.5)
```

`Probabilistic` モデル `model` をラップし、バイナリ分類をサポートすることを前提として、指定された `threshold` を正のクラス確率に適用することで `Deterministic` モデルとして扱います。従来の教師あり分類器に加えて、正規化スコアを予測する外れ値検出モデルにも適用できます - つまり、`AbstractProbabilisticUnsupervisedDetector` または `AbstractProbabilisticSupervisedDetector` をサブタイプとするモデルです。

慣例として、正のクラスは `levels(y)` によって返される2番目のクラスであり、ここで `y` はターゲットです。

`threshold=0.5` の場合、ラップされたモデルで `predict` を呼び出すことは、原子モデルで `predict_mode` を呼び出すことと同等です。

# 例

以下は、よく知られた Pima Indian diabetes データセットへの適用例であり、`threshold` パラメータの最適化を含み、高いバランス精度を目標としています。ターゲットクラスの分布は、500 の正例と 268 の負例です。

データの読み込み:

```julia
using MLJ, Random
rng = Xoshiro(123)

diabetes = OpenML.load(43582)
outcome, X = unpack(diabetes, ==(:Outcome), rng=rng);
y = coerce(Int.(outcome), OrderedFactor);
```

確率的分類器の選択:

```julia
EvoTreesClassifier = @load EvoTreesClassifier
prob_predictor = EvoTreesClassifier()
```

`TunedModel` でラップして、`threshold` を新しいハイパーパラメータとして持つ決定論的分類器を取得します:

```julia
point_predictor = BinaryThresholdPredictor(prob_predictor, threshold=0.6)
Xnew, _ = make_moons(3, rng=rng)
mach = machine(point_predictor, X, y) |> fit!
predict(mach, X)[1:3] # [0, 0, 0]
```

パフォーマンスの推定:

```julia
balanced = BalancedAccuracy(adjusted=true)
e = evaluate!(mach, resampling=CV(nfolds=6), measures=[balanced, accuracy])
e.measurement[1] # 0.405 ± 0.089
```

バランス精度を最大化する `threshold` を学習するためのチューニング戦略でラップします:

```julia
r = range(point_predictor, :threshold, lower=0.1, upper=0.9)
tuned_point_predictor = TunedModel(
    point_predictor,
    tuning=RandomSearch(rng=rng),
    resampling=CV(nfolds=6),
    range = r,
    measure=balanced,
    n=30,
)
mach2 = machine(tuned_point_predictor, X, y) |> fit!
optimized_point_predictor = report(mach2).best_model
optimized_point_predictor.threshold # 0.260
predict(mach2, X)[1:3] # [1, 1, 0]
```

自動しきい値モデルのパフォーマンスを推定します（ここではネストされたリサンプリング）:

```julia
e = evaluate!(mach2, resampling=CV(nfolds=6), measure=[balanced, accuracy])
e.measurement[1] # 0.477 ± 0.110
```
