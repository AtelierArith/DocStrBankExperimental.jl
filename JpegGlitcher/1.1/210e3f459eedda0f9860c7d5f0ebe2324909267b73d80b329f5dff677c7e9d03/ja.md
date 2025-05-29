```
glitch(img::AbstractMatrix; rng::AbstractRNG=default_rng(), nflips::Integer=10, quality::Integer=100)
```

`glitch` は、画像を JPEGTurbo.jl を使用して圧縮された JPEG 形式に変換し、エンコードされた画像の一部のバイト（変更しても安全）をランダムに変更します。

## キーワード引数

  * `rng::AbstractRNG`: バイトを選択して変更するために使用される乱数生成器。
  * `n::Integer`: 変更するバイトの数。
  * `quality::Integer`: JPEG のエンコード品質（低いほど品質が悪くなります）。
