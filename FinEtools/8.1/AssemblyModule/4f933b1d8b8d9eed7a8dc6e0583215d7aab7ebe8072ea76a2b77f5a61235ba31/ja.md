```
startassembly!(self::SysvecAssembler{T}, ndofs_row::FInt) where {T<:Number}
```

アセンブリを開始します。

このメソッドはベクトルアセンブリのためのバッファを作成します。最初のassembleメソッドの呼び出しの前に呼び出す必要があります。

  * `elem_mat_nmatrices` = アセンブリ中に処理されることが期待される要素行列の数。
  * `ndofs_row`= 自由度の総数。

# 戻り値

  * `self`: 修正されたアセンブラ。
