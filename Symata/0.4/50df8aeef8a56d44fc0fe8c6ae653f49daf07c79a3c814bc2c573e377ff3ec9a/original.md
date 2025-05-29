```
@sym expr
```

Embed symata expression `expr` in Julia code.

Read and evaluate `expr` embedded in Julia code.

```
julia> a = 1       # Julia symbol `a`
julia> @sym a = 2  # Symata symbol
julia> a
1
julia> @sym a
2
```
