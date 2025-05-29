```
in_sample = InSample()
```

`InSample` リサンプリング戦略をインスタンス化し、`evaluate!`、`evaluate`、およびチューニングで使用します。この戦略では、トレインセットとテストセットは同じであり、`rows` キーワード引数で指定されたすべての観測値で構成されます。`rows` が指定されていない場合、提供されたすべての行が使用されます。

# 例

```julia
using MLJBase, MLJModels

X, y = make_blobs()  # テーブルとベクトル
model = ConstantClassifier()
train, test = partition(eachindex(y), 0.7)  # train:test = 70:30
```

インサンプル（トレーニング）損失を計算します：

```julia
evaluate(model, X, y, resampling=InSample(), rows=train, measure=brier_loss)
```

アウトオブサンプル損失を計算します：

```julia
evaluate(model, X, y, resampling=[(train, test),], measure=brier_loss)
```

または同等に：

```julia
evaluate(model, X, y, resampling=Holdout(fraction_train=0.7), measure=brier_loss)
```
