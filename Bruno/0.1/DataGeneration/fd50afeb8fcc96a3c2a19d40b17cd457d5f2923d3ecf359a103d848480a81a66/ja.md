```
LogDiffInput(nTimeStep, initial, volatility, drift)
LogDiffInput(;kwargs...)
```

`makedata()`によって、次の形の対数正規拡散プロセスからデータを合成するために使用されるパラメータを含みます。

$$
P_{t+1} = P_t \cdot e^{drift + volatility \cdot v}
$$

ここで、P_tは時刻tにおけるデータの値です。driftとvolatilityは、正規分布の平均と標準偏差を表します。上記の方程式は、vを標準正規分布からのサンプルとし、それをdriftとvolatilityの項によってシフトおよびスケールすることによって、これらをそのように表現しています。

## 引数

  * `nTimeStep`: 合成する時間ステップの数。
  * `initial`: 0時点での仮定された値。デフォルト: 100。
  * `volatility`: 暗示された時間期間に関する標準偏差としての価格のボラティリティ。デフォルトは0.3。
  * `drift`: ドリフトパラメータは、対数正規拡散プロセスの平均を、全体の暗示された時間期間に関して説明します（1年をシミュレーションする場合、ドリフトは年間期待リターンとなります）。デフォルトは0.02。

## 例

```julia
input1 = LogDiffInput(250, 100, .05, .1)

# デフォルト値で最初の入力を初期化
input2 = LogDiffInput(250)

# ゼロボラティリティで2番目の入力を初期化
kwargs = Dict(:nTimeStep=>250, :initial=>100, :volatility=>.05, :drift=>.1)
input3 = LogDiffInput(;kwargs...)
```
