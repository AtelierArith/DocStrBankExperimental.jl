```
LatinHypercube(gens = 1,
               popsize = 100,
               ntour = 2,
               ptour = 0.8.,
               interSampleWeight = 1.0,
               ae_power = 2,
               periodic_ae = false,
               rng=Random.GLOBAL_RNG)
```

ライブラリ [LatinHypercubeSampling.jl](https://github.com/MrUrq/LatinHypercubeSampling.jl) を使用して、グリッドベースのハイパーパラメータチューニング戦略をインスタンス化します。

最適化されたラテンハイパーキューブサンプリングプランは、Audze-Eglais関数の逆に基づく遺伝的最適化アルゴリズムを使用して作成されます。最適化は `nGenerations` の間実行され、評価のために `n` モデルを作成します。ここで `n` は対応する `TunedModel` インスタンスによって指定されます。例えば、

```
tuned_model = TunedModel(model=...,
                         tuning=LatinHypercube(...),
                         range=...,
                         measures=...,
                         n=...)
```

（完全なオプションについては [`TunedModel`](@ref) を参照してください。）

境界に沿ったクラスタリングを減少させるために、Audze-Eglais関数の周期的バージョンを使用するには、`periodic_ae = true` を指定します。

### サポートされている範囲:

単一の1次元範囲または1次元範囲のベクトルを指定できます。具体的には、`LatinHypercubeSampling` 検索において、`TunedModel` インスタンスの `range` フィールドは次のようにできます：

  * 単一の1次元範囲 - すなわち、`ParamRange` オブジェクト - `r`、`range` メソッドを使用して構築されたもの。
  * 上記の形式のオブジェクトの任意のベクトル

`NumericRange` と `NominalRange` の両方がサポートされており、ハイパーパラメータ値は範囲によって指定されたスケール（例：`r.scale = :log`）でサンプリングされます。
