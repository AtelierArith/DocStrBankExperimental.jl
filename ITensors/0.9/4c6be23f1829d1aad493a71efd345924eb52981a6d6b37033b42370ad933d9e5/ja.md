```
swapprime[!](A::ITensor, pl1::Int, pl2::Int; <keyword arguments>) -> ITensor
swapprime[!](A::ITensor, pl1 => pl2; <keyword arguments>) -> ITensor

swapprime(inds, pl1::Int, pl2::Int; <keyword arguments>)
swapprime(inds, pl1 => pl2; <keyword arguments>)
```

ITensorまたはインデックスのコレクションのプライムレベル`pl1`のインデックスを`pl2`に設定し、プライムレベル`pl2`のインデックスを`pl1`に設定します。

オプションで、指定されたキーワード引数を持つインデックスのみを変更します。

# 引数

  * `tags = nothing`: 指定された場合、`hastags(i, tags) == true`である場合にのみインデックス`i`を変更します。
  * `plev = nothing`: 指定された場合、`hasplev(i, plev) == true`である場合にのみインデックス`i`を変更します。

ITensor関数には、`f`と`f!`の2つのバージョンがあります。後者はITensorをインプレースで変更します。両方のバージョンで、ITensorのストレージは変更されず、コピーされません（したがって、元のストレージのビューを持つITensorを返します）。
