```julia
plackettburman(matrix_size::Int64) -> Matrix{Int64}

```

指定されたサイズ `matrix_size` のプラケット・バーマンデザインを構築します。可能であれば、または可能な最大の最も近い数にします。

```jldoctest
julia> plackettburman(4)
8×7 Matrix{Int64}:
  1   1   1   1   1   1   1
 -1   1  -1   1   1  -1  -1
  1  -1   1   1  -1  -1  -1
 -1   1   1  -1  -1  -1   1
  1   1  -1  -1  -1   1  -1
  1  -1  -1  -1   1  -1   1
 -1  -1  -1   1  -1   1   1
 -1  -1   1  -1   1   1  -1

```
