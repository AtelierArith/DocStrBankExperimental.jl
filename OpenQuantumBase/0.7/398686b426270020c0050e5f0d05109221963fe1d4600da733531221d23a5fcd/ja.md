```
two_local_term(j, idx, num_qubit; sp=false)
```

$$
∑Jᵢⱼσᵢᶻσⱼᶻ
$$

の形の局所ハミルトニアンを構築します。`idx`はすべての二局所項のインデックスであり、`j`は対応する重みのリストです。`num_qubit`は量子ビットの総数です。`sp`がtrueに設定されている場合、スパース行列を生成します。

# 例

```julia-repl
julia> two_local_term([1.0, 0.5], [[1,2], [1,3]], 3) == σz⊗σz⊗σi + 0.5σz⊗σi⊗σz
true
```
