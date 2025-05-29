```
XPRSslpgetcoefs(prob, rowind, colind)::ncoefs, rowind, colind
```

問題における非線形係数の位置のリストを取得します。

この関数の簡易版については、XSLPgetformularowsを参照してください。

# 引数

  * `prob::XPRSprob`: 現在のSLP問題。
  * `rowind::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: 係数の行位置を返すために使用される整数配列。この引数に`XPRS_ALLOC`を渡すことで、関数が適切なサイズの配列を自動的に割り当てます。この引数に`nothing`を渡すことで、その情報を問い合わせないことができます。
  * `colind::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: 係数の列位置を返すために使用される整数配列。この引数に`XPRS_ALLOC`を渡すことで、関数が適切なサイズの配列を自動的に割り当てます。この引数に`nothing`を渡すことで、その情報を問い合わせないことができます。

# 戻り値

  * `ncoefs::Int32`: 問題における非線形係数の総数を返すために使用される整数。
  * `rowind::Union{Nothing,AbstractVector{Int32}}`: 係数の行位置を返すために使用される整数配列。
  * `colind::Union{Nothing,AbstractVector{Int32}}`: 係数の列位置を返すために使用される整数配列。

C APIの対応する関数[XPRSslpgetcoefs](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSslpgetcoefs.html)のドキュメントも参照してください。
