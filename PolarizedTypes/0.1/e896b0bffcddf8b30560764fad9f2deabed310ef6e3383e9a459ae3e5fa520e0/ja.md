```julia
struct StokesParams{T} <: StaticArraysCore.FieldVector{4, T}
```

偏光された複素視認性のストークスパラメータを保持する静的ベクトル

`StokesParams` と `CoherencyMatrix` の間で変換するには、`convert` 関数を使用します。

```julia
convert(::CoherencyMatrix, StokesVector(1.0, 0.1, 0.1, 0.4))
```
