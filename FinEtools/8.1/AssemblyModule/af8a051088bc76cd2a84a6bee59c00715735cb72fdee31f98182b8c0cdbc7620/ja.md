```
startassembly!(self::SysvecAssembler, ndofs_row)
```

アセンブリを開始します。

このメソッドはベクトルアセンブリのためのバッファを作成します。最初の`assemble`メソッドの呼び出しの前に呼び出す必要があります。

`ndofs_row`= 自由度の総数。

# 戻り値

  * `self`: 修正されたアセンブラ。
