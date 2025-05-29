```
attime(h, t)
attime(t)
```

時刻 `t` におけるハミルトニアンを返します。

# 例

```julia
julia> h = rydberg_h(atoms; Ω=sin)
nqudits: 4
+
├─ ∑ 5.42e6/|x_i-x_j|^6 n_i n_j
└─ Ω(t) ⋅ ∑ σ^x_i

julia> h |> attime(0.1)
nqudits: 4
+
├─ ∑ 5.42e6/|x_i-x_j|^6 n_i n_j
└─ 0.0499 ⋅ ∑ σ^x_i
```
