```
TimeCorrelationLogger(observableA::Function, observableB::Function,
                        TA::DataType, TB::DataType,
                        observable_length::Integer, n_correlation::Integer)
```

時間相関ロガー。

正規化された形の統計的相関を推定します。

$$
C(t)=\frac{\langle A_t\cdot B_0\rangle -\langle A\rangle\cdot \langle B\rangle}{\sqrt{\langle |A|^2\rangle\langle |B|^2\rangle}}
$$

または非正規化された形の

$$
C(t)=\langle A_t\cdot B_0\rangle -\langle A \rangle\cdot \langle B\rangle
$$

これらは統計的誤差を推定するため、またはグリーン-クーボ型の式から輸送係数を計算するために使用できます。*A*と*B*は、`observable(sys::System, neighbors; n_threads::Integer)`の形の関数である観測量です。*A*と*B*の戻り値はスカラーまたはベクトル型（位置や速度のような`Vector{SVector{...}}`を含む）であることができ、`dot`を実装する必要があります。

`n_correlation`は通常、`dt * n_correlation > t_corr`となるように選択する必要があります。ここで、`dt`はシミュレーションのタイムステップで、`t_corr`は考慮されるシステムと観測量のデコリレーション時間です。数値的安定性の目的のために、ロガーは内部的に合計を記録し、移動平均を実行しません。相関関数の正規化された形と非正規化された形は、`values(logger::TimeCorrelationLogger; normalize::Bool)`を通じて取得できます。

# 引数

  * `observableA::Function`: 観測量Aに対応する関数。
  * `observableB::Function`: 観測量Bに対応する関数。
  * `TA::DataType`: `observableA`が返す型で、`zero(TA)`をサポートします。
  * `TB::DataType`: `observableB`が返す型で、`zero(TB)`をサポートします。
  * `observable_length::Integer`: 観測量がベクトルの場合の長さ、またはスカラー値の場合は`1`。
  * `n_correlation::Integer`: 計算された相関ベクトルの長さ。
