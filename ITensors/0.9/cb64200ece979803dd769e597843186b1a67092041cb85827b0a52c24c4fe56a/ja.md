```
removetags[!](A::ITensor, ts::String; <keyword arguments>) -> ITensor

removetags(inds, ts::String; <keyword arguments>)
```

ITensorまたはインデックスのコレクションからタグ`ts`を削除します。

オプションで、指定されたキーワード引数を使用してのみインデックスを変更します。

# 引数

  * `tags = nothing`: 指定された場合、`hastags(i, tags) == true`の場合にのみインデックス`i`を変更します。
  * `plev = nothing`: 指定された場合、`hasplev(i, plev) == true`の場合にのみインデックス`i`を変更します。

ITensor関数には、`f`と`f!`の2つのバージョンがあります。後者はITensorをインプレースで変更します。どちらのバージョンでも、ITensorのストレージは変更されず、コピーされません（したがって、元のストレージのビューを持つITensorを返します）。
