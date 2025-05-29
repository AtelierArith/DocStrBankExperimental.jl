```
split_library(library::SpectralLibrary, split_fraction::Float64)
```

`SpectralLibrary`を指定された全スペクトルの割合に基づいて2つの新しいライブラリに分割します。

# 戻り値

  * 各出力ライブラリが元のライブラリのランダムで相互排他的なサブセットを含む`Tuple{SpectralLibrary, SpectralLibrary}`。それぞれ`split_fraction`と`1 - split_fraction`のスペクトルを含みます。

# 注意事項

  * 分割はランダムです。同じ`library`での連続した呼び出しは異なる結果をもたらす可能性があります。
