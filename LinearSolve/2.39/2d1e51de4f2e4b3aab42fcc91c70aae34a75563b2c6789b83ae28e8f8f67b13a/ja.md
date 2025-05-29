`GenericLUFactorization(pivot=LinearAlgebra.RowMaximum())`

Juliaの組み込みの一般的なLU因子分解。`LinearAlgebra.generic_lufact!`を呼び出すのと同等です。任意の数値型をサポートしますが、BLASベースのLU実装ほどのスケーリングは達成できません。オーバーヘッドが低く、小さな行列に適しています。

## 位置引数

  * pivot: ピボッティングの選択。デフォルトは`LinearAlgebra.RowMaximum()`です。もう一つの選択肢は`LinearAlgebra.NoPivot()`です。
