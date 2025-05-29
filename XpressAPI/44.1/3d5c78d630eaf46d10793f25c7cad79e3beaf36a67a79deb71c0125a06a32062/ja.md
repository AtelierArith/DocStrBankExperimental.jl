```
XPRSgetpresolvebasis(prob, rowstat, colstat)::rowstat, colstat
```

ユーザーのデータ領域に現在の基底をメモリから返します。

問題が事前解決されている場合、事前解決された基底が返されます。そうでない場合は、元の基底が返されます。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `rowstat::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: 各行に関連するスタックの基底状態、余剰変数または人工変数の整数配列（長さはROWS）。この引数に`XPRS_ALLOC`を渡すことで、関数が適切なサイズの配列を自動的に割り当てます。この引数に`nothing`を渡すことで、その情報を照会しないこともできます。
  * `colstat::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: 制約行列の列の基底状態を保持する整数配列（長さはCOLS）。この引数に`XPRS_ALLOC`を渡すことで、関数が適切なサイズの配列を自動的に割り当てます。この引数に`nothing`を渡すことで、その情報を照会しないこともできます。

# 戻り値

  * `rowstat::Union{Nothing,AbstractVector{Int32}}`: 各行に関連するスタックの基底状態、余剰変数または人工変数の整数配列（長さはROWS）。
  * `colstat::Union{Nothing,AbstractVector{Int32}}`: 制約行列の列の基底状態を保持する整数配列（長さはCOLS）。

C APIの対応する関数[XPRSgetpresolvebasis](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetpresolvebasis.html)のドキュメントも参照してください。
