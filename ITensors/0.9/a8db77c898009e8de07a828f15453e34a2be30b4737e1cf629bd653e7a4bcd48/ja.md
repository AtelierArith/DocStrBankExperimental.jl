```
replaceprime[!](A::ITensor, plold::Int, plnew::Int; <keyword arguments>) -> ITensor
replaceprime[!](A::ITensor, plold => plnew; <keyword arguments>) -> ITensor
mapprime[!](A::ITensor, <arguments>; <keyword arguments>) -> ITensor

replaceprime(inds, plold::Int, plnew::Int; <keyword arguments>)
replaceprime(inds::IndexSet, plold => plnew; <keyword arguments>)
mapprime(inds, <arguments>; <keyword arguments>)
```

ITensorまたはプライムレベル`plold`のインデックスのコレクションのインデックスのプライムレベルを`plnew`に設定します。

オプションで、指定されたキーワード引数を使用してインデックスのみを変更します。

# 引数

  * `tags = nothing`: 指定された場合、`hastags(i, tags) == true`の場合にのみインデックス`i`を変更します。
  * `plev = nothing`: 指定された場合、`hasplev(i, plev) == true`の場合にのみインデックス`i`を変更します。

ITensor関数には、`f`と`f!`の2つのバージョンがあります。後者はITensorをインプレースで変更します。両方のバージョンで、ITensorのストレージは変更されず、コピーされません（したがって、元のストレージのビューを持つITensorを返します）。
