```
RegressionGSA(; rank::Bool = false)
```

  * `rank::Bool = false`: ランク回帰分析を実行するかどうかを決定するフラグ

これを `gsa` に提供すると、次の統計量が計算され、`RegressionGSAResult` として提供されます。分析対象の関数 `f` が次元性 $f: R^n -> R^m$ の場合、これらの係数は行列として返され、対応する統計量は `(i, j)` のエントリに格納されます。

  * `pearson`: これは入力と出力の間の相関係数行列に相当します。ランク版はスピアマン係数として知られています。
  * `standard_regression`: 標準回帰係数、またはシグマ正規化導関数として知られています
  * `partial_correlation`: 精度行列に関連する部分相関係数であり、線形モデルの相関の測定値です

## メソッドの詳細

サンプルサイズ n が十分に大きい場合（少なくとも n > d）、X の値に基づいて Y の挙動を説明する線形モデルを適合させることが可能です。

GlobalSensitivity.jl によって提供されるこの分析のための測定値は次のとおりです。

a) ピアソン相関係数：

$$
r = \frac{\sum_{i=1}^{n} (x_i - \overline{x})(y_i - \overline{y})}{\sqrt{\sum_{i=1}^{n} (x_i - \overline{x})^2(y_i - \overline{y})^2}}
$$

b) 標準回帰係数 (SRC)：

$$
SRC_j = \beta_{j} \sqrt{\frac{Var(X_j)}{Var(Y)}}
$$

ここで $\beta_j$ は $X\_j$ に関連する線形回帰係数です。これはシグマ正規化導関数としても知られています。

c) 部分相関係数 (PCC)：

$$
PCC_j = \rho(X_j - \hat{X_{-j}},Y_j - \hat{Y_{-j}})
$$

ここで $\hat{X_{-j}}$ は線形モデルの予測であり、他の入力に対する $X_{j}$ を表し、$\hat{Y_{-j}}$ は $X_j$ が存在しない場合の線形モデルの予測です。PCC は他の入力の影響がキャンセルされたときの $Y$ に対する $X_j$ の感度を測定します。

`rank` が `true` に設定されている場合、ランク係数も計算されます。

## API

```
gsa(f, method::RegressionGSA, p_range::AbstractVector; samples::Int, batch = false)
gsa(X, Y, method::RegressionGSA)
```

### 例

```julia
using GlobalSensitivity

function linear_batch(X)
    A= 7
    B= 0.1
    @. A*X[1,:]+B*X[2,:]
end
function linear(X)
    A= 7
    B= 0.1
    A*X[1]+B*X[2]
end

p_range = [[-1, 1], [-1, 1]]
reg = gsa(linear_batch, RegressionGSA(), p_range; batch = true)

reg = gsa(linear, RegressionGSA(), p_range; batch = false)
reg = gsa(linear, RegressionGSA(true), p_range; batch = false) #ランク係数あり

X = QuasiMonteCarlo.sample(1000, [-1, -1], [1, 1], QuasiMonteCarlo.SobolSample())
Y = reshape(linear.([X[:, i] for i in 1:1000]), 1, 1000)
reg_mat = gsa(X, Y, RegressionGSA(true))
```
