```
SimultaneousLin(expr_fct::Ef,x1::Real,x2::Real, e::ErrorType; ConcavityChanges = [Inf]::Array{Float64,1} )
```

x1からx2までのexpr_fctの最適な区分線形の下限推定と上限推定のペアを作成し、同じブレークポイントを共有します。

# 引数

  * `expr_fct` : 線形化する関数（式またはネイティブのJulia関数のいずれか）
  * `x1` : 開始点
  * `x2` : 終了点
  * `e` : エラータイプ。Absolute()とRelative()の両方が実装されています。

# オプション引数

  * `ConcavityChanges` : 関数の凹凸の変化。指定しない場合は自動的に計算されますが、稀に凹凸がゼロに漸近する場合に精度エラーが発生する可能性があります。

!!! note
    `HeuristicLin()`と`ExactLin()`のどちらのアルゴリズムを使用するかを、エラータイプの後に単に追加することで指定することも可能です。デフォルトではPiecewiseLinApproxはヒューリスティックを使用します。

