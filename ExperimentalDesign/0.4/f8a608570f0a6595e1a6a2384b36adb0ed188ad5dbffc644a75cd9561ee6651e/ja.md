```julia
paley(matrix::Matrix{Int64}) -> Matrix{Int64}

```

[パレイ構成](https://en.wikipedia.org/wiki/Paley_construction)は、有限体を使用してアダマール行列を構築するための方法です。

```jldoctest
julia> paley(Matrix{Int}(undef, 8, 8))
8×8 Matrix{Int64}:
 -1   1   1  -1   1   1   1  -1
  1   1  -1   1   1   1  -1  -1
  1  -1   1   1   1  -1  -1   1
 -1   1   1   1  -1  -1   1   1
  1   1   1  -1  -1   1   1  -1
  1   1  -1  -1   1   1  -1   1
  1  -1  -1   1   1  -1   1   1
 -1  -1   1   1  -1   1   1   1

```
