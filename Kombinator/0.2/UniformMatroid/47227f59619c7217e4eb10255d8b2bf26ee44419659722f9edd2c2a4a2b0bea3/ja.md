一様マトロイド問題のインスタンスです。これは時々 m-セット問題と呼ばれます。

`m` 個以下の任意のセットが解となります。より正式には、独立したセットは最大 `m` 要素を含むセットです。

次のように形式化できます：

$$
\max \sum_i \mathrm{rewards}_i x_i
$$

$\mathrm{s.t.} \sum_i x_i \leq m, \quad x \in \{0, 1\}^d$
