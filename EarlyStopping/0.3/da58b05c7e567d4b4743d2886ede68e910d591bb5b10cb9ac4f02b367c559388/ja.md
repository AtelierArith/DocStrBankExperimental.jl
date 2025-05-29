```
PQ(; alpha=0.75, k=5, tol=eps(Float64))
```

反復的な教師あり学習者のトレーニングのための停止基準。

停止は、プレヒルトの進捗修正一般化損失が閾値 $PQ_T > alpha$ を超えたとき、またはトレーニングの進捗が $P_j ≤ tol$ に低下したときにトリガーされます。ここで `k` はトレーニング進捗を推定するために使用されるトレーニング（インサンプル）損失の数です。

## コンテキストと用語の説明

時刻 $j$ における*トレーニング進捗*は次のように定義されます。

$$
P_j = 1000 |M - m|/|m|
$$

ここで、$M$ は最後の `k` 個のトレーニング損失 $F_1, F_2, …, F_k$ の平均であり、$m$ はそれらの損失の最小値です。

時刻 $t$ における*進捗修正一般化損失*は次のように与えられます。

$$
PQ_t = GL_t / P_t
$$

ここで、$GL_t$ は時刻 $t$ における一般化損失です；参照してください [`GL`](@ref)。

PQ は次の条件が真であるときに停止します：

1. `done!(c::PQ, loss; training = true)` または `update_training(c::PQ, loss, state)` を介して少なくとも `k` 個のトレーニングサンプルが収集されている。
2. 最後の更新がアウトオブサンプルの更新である。(`done!(::PQ, loss; training=true)` は常に偽です)
3. 進捗修正一般化損失が閾値 $PQ_t > alpha$ を超える **または** トレーニング進捗が停滞する $P_j ≤ tol$。

参考文献: [Prechelt, Lutz (1998): "Early Stopping- But When?", in *Neural Networks: Tricks of the Trade*, ed. G. Orr, Springer.](https://link.springer.com/chapter/10.1007%2F3-540-49430-8_3).
