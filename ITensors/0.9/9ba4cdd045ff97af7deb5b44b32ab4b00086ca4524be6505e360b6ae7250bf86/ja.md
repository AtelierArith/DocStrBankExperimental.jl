```
prime[!](A::ITensor, plinc::Int = 1; <keyword arguments>) -> ITensor

prime(inds, plinc::Int = 1; <keyword arguments>) -> IndexSet
```

ITensorまたはインデックスのコレクションのインデックスのプライムレベルを増加させます。

オプションで、指定されたキーワード引数でのみインデックスを変更します。

# 引数

  * `tags = nothing`: 指定された場合、`hastags(i, tags) == true` の場合にのみインデックス `i` を変更します。
  * `plev = nothing`: 指定された場合、`hasplev(i, plev) == true` の場合にのみインデックス `i` を変更します。

ITensor関数には、`f` と `f!` の2つのバージョンがあります。後者はITensorをインプレースで変更します。どちらのバージョンでも、ITensorのストレージは変更されず、コピーされません（したがって、元のストレージのビューを持つITensorを返します）。
