```
C_iio_create_scan_block(backend, flags)
```

スキャンブロックを作成します。

# パラメータ

  * `backend::String`: スキャンに使用するバックエンドを含むNULL終端文字列。NULLの場合、利用可能なすべてのバックエンドが使用されます。
  * `flags::UInt32` : 現在は未使用。0に設定します。

# 戻り値

  * 成功した場合、`iio_scan_block`構造体へのポインタ
  * 失敗した場合、NULLが返され、errnoが適切に設定されます

バージョン0.20で導入されました。

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Scan.html#gad7fd2ea05bf5a8cebaff26b60edb8a13)
