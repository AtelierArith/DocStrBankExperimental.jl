```
padded_tilesize(T::Type, kernelsize::Dims, [ncache=2]) -> tilesize::Dims
```

`kernelsize`のサイズに基づいて、生産的な作業量を最大化するための適切なタイルサイズを計算します。配列の要素タイプは`T`です。オプションで、L1キャッシュに同時に収まるようにしたい配列の数`ncache`を指定できます。

これは、最初の次元を大きくすることを優先します。なぜなら、最初の次元は個々のキャッシュラインに対応するからです。

# 例

julia> padded_tilesize(UInt8, (3,3)) (768,18)

julia> padded_tilesize(UInt8, (3,3), 4) (512,12)

julia> padded_tilesize(Float64, (3,3)) (96,18)

julia> padded_tilesize(Float32, (3,3,3)) (64,6,6) ```
