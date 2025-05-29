```
scale_factor(transform::AbstractTransform, A, [dims = 1:ndims(A)])
```

与えられた配列を指定された次元 `dims`（デフォルトではすべての次元）に沿って変換した後に正規化するために必要な係数を取得します。

配列 `A` は変換入力の次元を持っている必要があります。

**重要**: 次元 `dims` は [`plan`](@ref) に渡されたものと同じでなければなりません。

# 例

```jldoctest scale_factor
julia> C = zeros(ComplexF32, 3, 4, 5);

julia> scale_factor(Transforms.FFT(), C)
60

julia> scale_factor(Transforms.BFFT(), C)
60

julia> scale_factor(Transforms.BFFT(), C, 2:3)
20

julia> R = zeros(Float64, 3, 4, 5);

julia> scale_factor(Transforms.RFFT(), R, 2)
4

julia> scale_factor(Transforms.RFFT(), R, 2:3)
20

julia> scale_factor(Transforms.BRFFT(8), C)
96

julia> scale_factor(Transforms.BRFFT(9), C)
108
```

これは失敗します。なぜなら `RFFT` の入力は実数であり、`R` は複素配列だからです：

```jldoctest scale_factor
julia> scale_factor(Transforms.RFFT(), C, 2:3)
ERROR: MethodError: no method matching scale_factor(::PencilFFTs.Transforms.RFFT, ::Array{ComplexF32, 3}, ::UnitRange{Int64})
```
