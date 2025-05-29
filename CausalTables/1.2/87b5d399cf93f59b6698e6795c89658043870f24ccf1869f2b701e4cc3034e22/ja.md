```
additive_mtp(δ)
```

定数（または定数ベクトル）δを`CausalTable`オブジェクトの処置変数に加える関数を構築します。この関数は`ape`への引数として使用されることを意図しています。

# 引数

  * δ: `CausalTable`の処置変数に適用される「加法シフト」。

# 戻り値

  * `CausalTable`オブジェクトを入力として受け取り、δ単位シフトされた処置の列テーブルを返す関数。

# 例

```@example
using Distributions
dgp = @dgp(
    L ~ Beta(2, 4),
    A ~ @.(Normal(L)),
    Y ~ @.(Normal(A + 2 * L + 1))
)
scm = StructuralCausalModel(dgp, [:A], [:Y], [:L])
ape(scm, additive_mtp(0.5))
```
