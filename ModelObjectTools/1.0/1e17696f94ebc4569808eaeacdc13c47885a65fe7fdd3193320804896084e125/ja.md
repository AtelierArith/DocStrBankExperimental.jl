addVarInfo(varName::Symbol; lb = -Inf, ub = Inf, normalization::Symbol = :none)

この関数を使用して、モデルオブジェクト（パラメータセット、内生変数のセットなど）を定義する構造体のフィールドに対応する変数名を登録します。各変数について、許可される値の範囲は [lb, ub] です。

境界が必要ない場合は、デフォルトオプションを使用します: lb = -Inf, ub = Inf。

許可される正規化値は次のとおりです：

  * :sumToOne     （一次元配列用）
  * :firstIsZero  （一次元配列用）
  * :firstIsOne   （一次元配列用）
  * :ordered      （一次元配列または行列用。行列の場合、列に沿って値が増加する必要があります）
  * :none         （デフォルトオプション）
