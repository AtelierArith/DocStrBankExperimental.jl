```
isobands(xs::Vector{Float64}, ys::Vector{Float64}, zs::Matrix{Float64}, low_values::Vector{Float64}, high_values::Vector{Float64})
```

行列 `zs` から `low_values` と `high_values` のすべてのペアに対して等高線のベクトルを作成します。`zs` の行は `ys` の線形間隔の値に対応し、列は `xs` に対応します。返されるベクトルの各エントリは、2つの Vector{Float64} フィールド `x` と `y` を持つ NamedTuple と、Vector{Int} フィールド `id` です。各ユニークな id は1つのポリゴンを示し、ポリゴンは外部ポリゴンまたは穴であり、特に順序はありません。したがって、プロットパッケージに供給するために後処理が必要です。
