```
replacetags[!](A::ITensor, tsold::String, tsnew::String; <keyword arguments>) -> ITensor

replacetags(is::IndexSet, tsold::String, tsnew::String; <keyword arguments>) -> IndexSet
```

ITensorのインデックスに対して、タグ`tsold`を`tsnew`に置き換えます。

オプションとして、指定されたキーワード引数を持つインデックスのみを変更します。

# 引数

  * `tags = nothing`: 指定された場合、`hastags(i, tags) == true`である場合にのみインデックス`i`を変更します。
  * `plev = nothing`: 指定された場合、`hasplev(i, plev) == true`である場合にのみインデックス`i`を変更します。

ITensor関数には、`f`と`f!`の2つのバージョンがあります。後者はITensorをインプレースで変更します。どちらのバージョンでも、ITensorのストレージは変更されず、コピーされません（したがって、元のストレージのビューを持つITensorを返します）。
