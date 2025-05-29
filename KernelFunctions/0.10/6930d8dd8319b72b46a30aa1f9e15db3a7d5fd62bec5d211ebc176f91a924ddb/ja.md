```
prepare_isotopic_multi_output_data(x::AbstractVector, y::ColVecs)
```

`N = length(x)` の入力 `x` のコレクションと、ベクトルのベクトル `y`（`ColVecs` によって効率的に表現される）を、マルチ出力カーネルで使用するのに適した形式に変換するためのユーティリティ機能です。

`y[n]` は、入力 `x[n]` に対応するベクトル値の出力です。したがって、`length(x) == length(y)` である必要があります。

例えば、出力が最初に `num_outputs × N` 行列に格納されている場合：

```julia
julia> x = [1.0, 2.0, 3.0];

julia> Y = [1.1 2.1 3.1; 1.2 2.2 3.2]
2×3 Matrix{Float64}:
 1.1  2.1  3.1
 1.2  2.2  3.2

julia> inputs, outputs = prepare_isotopic_multi_output_data(x, ColVecs(Y));

julia> inputs
6-element KernelFunctions.MOInputIsotopicByFeatures{Float64, Vector{Float64}, Int64}:
 (1.0, 1)
 (1.0, 2)
 (2.0, 1)
 (2.0, 2)
 (3.0, 1)
 (3.0, 2)

julia> outputs
6-element Vector{Float64}:
 1.1
 1.2
 2.1
 2.2
 3.1
 3.2
```

他にも [`prepare_heterotopic_multi_output_data`](@ref) を参照してください。
