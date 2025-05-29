```
XPRS_ge_getlasterror(maxbytes)::msgcode, msg, nbytes
```

Xpressグローバル環境への呼び出し中に発生した最後のエラーを返します。

# 引数

  * `maxbytes::Integer`: 文字バッファ`msg`のサイズ。

# 戻り値

  * `msgcode::Int32`: エラーコードが返されるメモリ位置。
  * `msg::AbstractString`: グローバル環境に関連する最後のエラーメッセージが返されるサイズ`maxbytes`の文字バッファ。
  * `nbytes::Int32`: 完全なエラーストリングを保持するために必要なバッファの最小サイズが返されるメモリ位置。

C APIの対応する関数[XPRS*ge*getlasterror](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRS_ge_getlasterror.html)のドキュメントも参照してください。
