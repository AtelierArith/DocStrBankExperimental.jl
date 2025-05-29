```
read_namedmatrix(filepath::String, valuetype::Type = FLoat64filepath::String, valuetype::Type)
```

名前付きインデックスを持つ行列をNamedArrayとして読み込みます。

# 引数

  * `filepath::String` : 読み込む行列のファイルパス
  * `delimiter::Char` : 行列内の値の間の区切り文字（デフォルト = ' '）
  * `valuetype::Type` : 行列に含まれる値の型（デフォルト = Float64）
