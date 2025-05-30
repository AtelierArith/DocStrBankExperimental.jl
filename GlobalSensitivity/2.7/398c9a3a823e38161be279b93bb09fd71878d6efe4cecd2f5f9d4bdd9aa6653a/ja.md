```
DeltaMoment(; nboot = 500, conf_level = 0.95, Ygrid_length = 2048,
                 num_classes = nothing)
```

  * `nboot`: ブートストラップの繰り返し回数。デフォルトは `500`。
  * `conf_level`: ブートストラップによる信頼区間計算に使用されるレベル。デフォルト値は `0.95`。
  * `Ygrid_length`: カーネル密度推定と積分ステップを実行する際に考慮する数値積分点の数。カーネル密度推定における効率的なFFTのために2の累乗である必要があります。デフォルトは `2048`。
  * `num_classes`: モデル出力の分布をクラスに条件付けて生成する際に、各因子を分割するクラスの数を決定します。

## メソッドの詳細

デルタモーメント非依存メソッドは、密度ベースの統計のための新しい推定量に依存しています。これは、分布ベースの感度測定と特定のモーメントへの寄与を考慮した感度測定の両方の推定を可能にします。このメソッドの主な利点の1つは、計算コストがパラメータの数に依存しないことです。

!!! note
    `DeltaMoment` はスカラー出力にのみ機能します。


## API

```
gsa(f, method::DeltaMoment, p_range; samples, batch = false,
         rng::AbstractRNG = Random.default_rng())
gsa(X, Y, method::DeltaMoment; rng::AbstractRNG = Random.default_rng())
```

### 例

```julia
using GlobalSensitivity, Test

function ishi(X)
    A= 7
    B= 0.1
    sin(X[1]) + A*sin(X[2])^2+ B*X[3]^4 *sin(X[1])
end

lb = -ones(3)*π
ub = ones(3)*π

m = gsa(ishi,DeltaMoment(),fill([lb[1], ub[1]], 3), samples=1000)


samples = 1000
X = QuasiMonteCarlo.sample(samples, lb, ub, QuasiMonteCarlo.SobolSample())
Y = ishi.(@view X[:, i] for i in 1:samples)

m = gsa(X, Y, DeltaMoment())
```
