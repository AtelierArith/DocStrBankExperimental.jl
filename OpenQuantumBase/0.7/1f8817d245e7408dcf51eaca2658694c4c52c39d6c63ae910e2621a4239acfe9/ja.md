```
local_field_term(h, idx, num_qubit; sp=false)
```

$$
∑hᵢσᵢᶻ
$$

の形の局所ハミルトニアンを構築します。`idx`はすべての局所場項のインデックスであり、`h`は対応する重みのリストです。`num_qubit`はキュービットの総数です。`sp`がtrueに設定されている場合、スパース行列を生成します。

# 例

```julia-repl
julia> local_field_term([1.0, 0.5], [1, 2], 2) == σz⊗σi+0.5σi⊗σz
true
```
