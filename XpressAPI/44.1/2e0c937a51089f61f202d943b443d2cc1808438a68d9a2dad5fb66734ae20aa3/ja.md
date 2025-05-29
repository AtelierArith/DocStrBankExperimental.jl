```
XPRSstrongbranch(prob, nbounds, colind, bndtype, bndval, iterlim, objval, status)::objval, status
```

指定されたすべての境界変更に対して強い分岐反復を実行します。

各候補境界変更について、`XPRSstrongbranch`は基礎LPの現在の最適解から開始して双対単純形反復を実行し、これらの反復後に達成されたステータスと目的値の両方を返します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `nbounds::Integer`: 試す境界変更の数。
  * `colind::AbstractVector{Integer}`: 境界が変更される列のインデックスを含むサイズ`nbounds`の整数配列。
  * `bndtype::AbstractVector{Cchar}`: 境界を変更するタイプを示す長さ`nbounds`の文字配列：Uは上限を変更することを示し、Lは下限を変更することを示し、Bは両方の境界を変更すること、すなわち列を固定することを示します。
  * `bndval::AbstractVector{Number}`: 新しい境界値を与える長さ`nbounds`の倍精度配列。
  * `iterlim::Integer`: 各境界変更に対して実行する最大LP反復回数。
  * `objval::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: 強い分岐反復を実行した後の各LPの目的値。この引数に`XPRS_ALLOC`を渡すことで、関数が適切なサイズの配列を割り当てることができます。この引数に`nothing`を渡すことで、その情報を照会しないことができます。
  * `status::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: 強い分岐反復を実行した後の各LPのステータス、LPSTATUS属性に詳細が記載されています。この引数に`XPRS_ALLOC`を渡すことで、関数が適切なサイズの配列を割り当てることができます。この引数に`nothing`を渡すことで、その情報を照会しないことができます。

# 戻り値

  * `objval::Union{Nothing,AbstractVector{Float64}}`: 強い分岐反復を実行した後の各LPの目的値。
  * `status::Union{Nothing,AbstractVector{Int32}}`: 強い分岐反復を実行した後の各LPのステータス、LPSTATUS属性に詳細が記載されています。

C APIの対応する関数[XPRSstrongbranch](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSstrongbranch.html)のドキュメントも参照してください。
