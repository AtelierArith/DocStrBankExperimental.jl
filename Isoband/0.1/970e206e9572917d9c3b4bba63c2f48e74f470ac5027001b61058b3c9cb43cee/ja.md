```
isolines(xs, ys, zs, value::Real)
```

行列 `zs` から `value` の1つの等高線を作成します。`zs` の行は `ys` の線形間隔での値に対応し、列は `xs` に対応します。`x` と `y` の2つの Vector{Float64} フィールドと、Vector{Int} フィールド `id` を持つ NamedTuple を返します。各ユニークな id は1つの線を示します。
