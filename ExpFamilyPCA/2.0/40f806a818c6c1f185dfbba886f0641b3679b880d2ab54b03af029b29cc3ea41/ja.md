```
decompress(epca::EPCA, A::AbstractMatrix{T}) where T <: Real
```

EPCAモデルを使用して圧縮された行列`A`を解凍します。

# 引数

  * `epca::EPCA`: フィットされたEPCAモデル。[1] `compress`の前に`fit!`を呼び出す必要があります。
  * `A::AbstractMatrix{T}`: (`n`, `outdim`) - 圧縮されたデータ行列。

# 戻り値

  * `X̂::AbstractMatrix{T}`: (`n`, `indim`) - EPCAモデルのパラメータを使用して近似された再構築されたデータ行列。

# 使用法

```julia
Y_reconstructed = decompress(epca, Y)
```
