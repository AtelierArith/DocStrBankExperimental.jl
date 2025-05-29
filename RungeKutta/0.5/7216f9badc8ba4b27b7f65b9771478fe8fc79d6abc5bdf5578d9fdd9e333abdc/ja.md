分割されたルンゲ-クッタ法の表

$$
\begin{aligned}
Q_{n,i} &= q_{n} + h \sum \limits_{j=1}^{s} a_{ij} \, v(t_{n} + c_j \Delta t, Q_{n,j}, P_{n,j}) , &
q_{n+1} &= q_{n} + h \sum \limits_{i=1}^{s} b_{i}  \, v(t_{n} + c_j \Delta t, Q_{n,i}, P_{n,i}) , \\
P_{n,i} &= p_{n} + h  \sum \limits_{i=1}^{s} \bar{a}_{ij} \, f(t_{n} + c_j \Delta t, Q_{n,j}, P_{n,j}) , &
p_{n+1} &= p_{n} + h \sum \limits_{i=1}^{s} \bar{b}_{i}   \, f(t_{n} + c_j \Delta t, Q_{n,i}, P_{n,i}) .
\end{aligned}
$$

パラメータ:

  * `T`: コエフィシエント配列のデータ型

フィールド:

  * `name`: 表の象徴的な名前
  * `o`: メソッドの次数
  * `s`: ステージの数
  * `q`: `q`のための表
  * `p`: `p`のための表
  * `R∞`: 無限大での安定性関数

実際の表は`q`と`p`に格納されています:

  * `a`: コエフィシエント $a_{ij}$ で $ 1 \le i,j \le s$
  * `b`: 重み $b_{i}$ で $ 1 \le i \le s$
  * `c`: ノード $c_{i}$ で $ 1 \le i \le s$

コンストラクタ:

```julia
PartitionedTableau{T}(name, o, q, p)
PartitionedTableau{T}(name, q, p)
PartitionedTableau(name::Symbol, q::Tableau, p::Tableau)
PartitionedTableau(name::Symbol, q::Tableau)
```
