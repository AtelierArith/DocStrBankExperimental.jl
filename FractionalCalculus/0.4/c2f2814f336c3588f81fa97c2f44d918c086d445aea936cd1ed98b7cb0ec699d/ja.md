# シンボリック分数積分

```
semiint(fun)
```

`semiint` は SymbolicUtils.jl と Symbolics.jl を使用してシンボリック分数積分を計算します。

### 例

```julia-repl
julia> using SymbolicUtils
julia> @syms x
julia> semiint(x^4)
0.45851597901024005(x^4.5)
```
