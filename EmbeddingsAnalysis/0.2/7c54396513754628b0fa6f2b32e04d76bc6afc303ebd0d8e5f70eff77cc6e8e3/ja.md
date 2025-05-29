```
compress(wv [;kwargs...])
```

`wv::WordVectors`を配列量子化を使用して圧縮します。

# キーワード引数

  * `sampling_ratio::AbstractFloat` は、量子化コードブック作成に使用するベクトルの割合を指定します。
  * `k::Int` は、コードブックの量子化値の数です。
  * `m::Int` は、使用するコードブックの数です。
  * `method::Symbol` は、配列量子化方法を指定します。
  * `distance::PreMetric` は、距離です。

量子化方法に特有の他のキーワード引数も提供できます。
