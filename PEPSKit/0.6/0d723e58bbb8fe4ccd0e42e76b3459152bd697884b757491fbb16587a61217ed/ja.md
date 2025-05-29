```julia
struct FixedSpaceTruncation <: TensorKit.TruncationScheme
```

CTMRG特有の`tsvd`のための切り捨てスキームで、SVDが実行されるボンド空間を固定します。異なる環境方向や単位セルのエントリが異なる空間を持つ可能性があるため、この切り捨てスタイルは`TruncationSpace`とは異なります。
