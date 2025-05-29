```
script(::Vector{UInt8}; type::Symbol=:P2WSH) -> Script
```

指定されたハッシュのセットタイプの`Script`を返します。

  * `type`は`:P2PKH`、`:P2SH`、`:P2WPKH`、または`:P2WSH`である必要があります
  * ハッシュはP2WSHスクリプトの場合は32バイト、他の場合は20バイトの長さでなければなりません
