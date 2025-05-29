```julia
struct FixedSpaceTruncation <: TensorKit.TruncationScheme
```

CTMRG specific truncation scheme for `tsvd` which keeps the bond space on which the SVD is performed fixed. Since different environment directions and unit cell entries might have different spaces, this truncation style is different from `TruncationSpace`.
