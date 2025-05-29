```
add_complex_vector_of_phase_variable!
```

モデル `m` に複素変数を追加します。インデックスは次の通りです。

1. `var_symbol` は `:v` のように
2. `bus_or_edge`
3. `time_step`  # TODO このメソッドで時間とバス*または*エッジのスワップはまだ行っていません
4. `[1, 2, 3]` のフェーズ

```julia
# 未定義のフェーズのためにゼロとして残る変数を初期化

m[var_symbol][bus_or_edge][time_step] = convert(
    Vector{GenericAffExpr{ComplexF64, VariableRef}}, 
    [0im; 0im; 0im]
)
```

上限と下限は、制約を使用して提供された場合に追加されます。
