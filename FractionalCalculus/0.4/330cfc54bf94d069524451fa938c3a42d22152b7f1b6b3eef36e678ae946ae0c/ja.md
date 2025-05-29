# シンボリック分数微分

```
semidiff(fun)
```

`semidiff` は SymbolicUtils.jl と Symbolics.jl を使用して、シンボリック分数微分を計算します。

### 例

```julia-repl
julia> using SymbolicUtils
julia> @syms x
julia> semidiff(log(x))
log(4x) / sqrt(πx)
```
