find*pure*growth*slope(t, E, time*range=nothing)

E ≈ E₀ * exp(γt) の形の指数関数フィットを推定します。

`(line, γ)` を返します。ここで、     - `γ` は指数成長率の最適フィット、     - `line` は `E₀ * exp.(γ .* t)` です。
