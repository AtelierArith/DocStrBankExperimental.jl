```
channelview(A)
```

は、`A`のビューを返し、必要に応じて`A`の色チャネルを新しい最初の次元に分割します。

RGBやBGRのような型に関連して、返される配列のチャネルは、メモリ順序ではなくコンストラクタ引数の順序になります（メモリ順序を使用したい場合は`reinterpretc`を参照してください）。

# 例

```julia
img = rand(RGB{N0f8}, 10, 10)
A = channelview(img)   # 3×10×10 配列
```

参照: [`colorview`](@ref)
