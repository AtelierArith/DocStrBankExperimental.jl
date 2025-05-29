```
AlmostBandedMatrix(bands::BandedMatrix, fill)
AlmostBandedMatrix{T}(bands, fill)
AlmostBandedMatrix(::UndefInitializer, [::Type{T} = Float64], mn::NTuple{2, Integer},
    lu::NTuple{2, Integer}, rank::Integer)
AlmostBandedMatrix{T}(::UndefInitializer, mn::NTuple{2, Integer},
    lu::NTuple{2, Integer}, rank::Integer)
```

`AlmostBandedMatrix`は、`bands`部分と`fill`部分を持つ行列です。効率的な操作のために、行列をBandedMatrixとして、重複部分を持つ別のAbstractMatrixとして保存します。

[3 3 3 2 2 2 2 ... 2 2 2] [3 3 3 3 2 2 2 ... 2 2 2] [0 1 1 1 1 0 0 ... 0 0 0] [0 0 1 1 1 1 0 ... 0 0 0] [.......................] [.......................] [.......................] [0 0 0 0 0 0 0 ... 1 1 0] [0 0 0 0 0 0 0 ... 1 1 1]

ここで、`2`はfill部分、`1`はbands部分、`3`は重複部分を表します。
