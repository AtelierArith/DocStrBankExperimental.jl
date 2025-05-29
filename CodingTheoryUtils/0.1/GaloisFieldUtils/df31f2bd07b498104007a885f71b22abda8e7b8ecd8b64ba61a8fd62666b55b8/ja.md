```
from_f2mat_to_intmat(M::Matrix{<:GaloisFields.AbstractGaloisField})::Matrix{Int}
```

ガロア体上の行列を整数行列に変換します。ここで、1は1にマッピングされ、0は0にマッピングされます。

# 引数

  * `M::Matrix{<:GaloisFields.AbstractGaloisField}`: ガロア体上の入力行列

# 戻り値

  * `Matrix{Int}`: 入力行列と同じ次元の整数行列

# 例

```julia
julia> F4, α = GaloisField(2, 2, :α)
julia> M = [F4(1) F4(0); F4(0) F4(1)]
julia> from_f2mat_to_intmat(M)
2×2 Matrix{Int64}:
 1  0
 0  1
```
