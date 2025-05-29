```
multiplicative_mtp(δ)
```

`CausalTable`オブジェクト内の処置変数を定数δでスケーリングする関数を構築します。この関数は`ape`への引数として使用することを意図しています。

# 引数

  * δ: `CausalTable`の処置変数に適用される「乗法シフト」。

# 戻り値

  * `CausalTable`オブジェクトを入力として受け取り、δ単位でスケーリングされた処置の列テーブルを返す関数。

# 例

```@example
using Distributions
dgp = CausalTables.@dgp(
    L ~ Beta(2, 4),
    A ~ @.(Normal(L)),
    Y ~ @.(Normal(A + 2 * L + 1))
)
scm = CausalTables.StructuralCausalModel(dgp, [:A], [:Y], [:L])
ape(scm, multiplicative_mtp(2.0))
```
