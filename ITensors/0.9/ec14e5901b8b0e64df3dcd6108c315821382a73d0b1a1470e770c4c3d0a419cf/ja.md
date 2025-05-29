```
swaptags[!](A::ITensor, ts1::String, ts2::String; <keyword arguments>) -> ITensor

swaptags(is::IndexSet, ts1::String, ts2::String; <keyword arguments>) -> IndexSet
```

ITensorのインデックスのタグ`ts1`を`ts2`と入れ替えます。

オプションとして、指定されたキーワード引数でのみインデックスを変更します。

# 引数

  * `tags = nothing`: 指定された場合、`hastags(i, tags) == true`である場合にのみインデックス`i`を変更します。
  * `plev = nothing`: 指定された場合、`hasplev(i, plev) == true`である場合にのみインデックス`i`を変更します。

ITensor関数には、`f`と`f!`の2つのバージョンがあります。後者はITensorをインプレースで変更します。どちらのバージョンでも、ITensorのストレージは変更されず、コピーされません（したがって、元のストレージのビューを持つITensorを返します）。
