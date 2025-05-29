```julia
redu(
    A::JunctionTrees.Factor{T},
    vars::Tuple,
    vals::Tuple
) -> JunctionTrees.Factor

```

`A`のすべてのエントリを、`vars`と`vals`で渡された証拠と一致しないものは削除/無効化します。ここで、`vars`の各変数には`vals`の対応する値が割り当てられます。

# 例

```jldoctest
A = Factor{Float64,3}((1, 2, 3), cat([0.25 0.08; 0.05 0.0; 0.15 0.09],
                                     [0.35 0.16; 0.07 0.0; 0.21 0.18], dims=3))
obs_vars = (3,)
obs_vals = (1,)
redu(A, obs_vars, obs_vals)

# 出力

Factor{Float64, 3}((1, 2, 3), [0.25 0.08; 0.05 0.0; 0.15 0.09;;; 0.0 0.0; 0.0 0.0; 0.0 0.0])
```
