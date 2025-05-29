```
get_stim_circuit(circuit::Vector{Layer}, gate_probabilities::Dict{Gate, Vector{Float64}}, noisy_prep::Bool, noisy_meas::Bool; extra_fields::Dict{Symbol, Any} = Dict{Symbol, Any}(), meas_and_reset::Bool = false)
```

回路 `circuit` の Stim 文字列表現と、`gate_probabilities` で指定されたエラー確率、`noisy_prep` が `true` の場合のノイズのある準備、`noisy_meas` が `true` の場合のノイズのある測定を返します。キュービットの座標は、[`CodeParameters`](@ref) オブジェクトを含む場合、`extra_fields` によって指定されます。リセットタイプは `reset_type` で指定され、`:reset`、`:meas`、または `:meas_reset` になります。

Stim は一量子ビットのパウリを次のように順序付けます: X, Y, Z。私たちは一量子ビットのパウリを次のように順序付けます: X, Z, Y。この順序を変換するためのインデックスは: 1, 3, 2 です。

Stim は二量子ビットのパウリを次のように順序付けます: IX, IY, IZ, XI, XX, XY, XZ, YI, YX, YY, YZ, ZI, ZX, ZY, ZZ。私たちは二量子ビットのパウリを次のように順序付けます: XI, IX, XX, ZI, YI, ZX, YX, IZ, XZ, IY, XY, ZZ, YZ, ZY, YY。この順序を変換するためのインデックスは: 4, 1, 5, 12, 8, 13, 9, 3, 7, 2, 6, 15, 11, 14, 10 です。私たちの順序から Stim の順序に変換するためのインデックスは: 2, 10, 8, 1, 3, 11, 9, 5, 7, 15, 13, 4, 6, 14, 12 です。
