```
rand([rng::AbstractRNG,] s::Sampleable)
```

`s`から1つのサンプルを生成します。

```
rand([rng::AbstractRNG,] s::Sampleable, n::Int)
```

`s`から`n`個のサンプルを生成します。返されるオブジェクトの形式は`s`の変量形式によって異なります：

  * `s`が単変量の場合、長さ`n`のベクトルを返します。
  * `s`が多変量の場合、`n`列の行列を返します。
  * `s`が行列変量の場合、各要素がサンプル行列である配列を返します。

    rand([rng::AbstractRNG,] s::Sampleable, dim1::Int, dim2::Int...)   rand([rng::AbstractRNG,] s::Sampleable, dims::Dims)

与えられた次元によって形状が決まる`s`からのサンプルの配列を生成します。
