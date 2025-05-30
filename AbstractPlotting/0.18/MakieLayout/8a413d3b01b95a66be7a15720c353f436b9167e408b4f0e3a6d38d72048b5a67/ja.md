```
layoutscene(nrows::Int, ncols::Int, padding = 30; kwargs...)
```

`campixel!` モードで `Scene` を作成し、サイズ `nrows` x `ncols` の `GridLayout` をシーンのピクセル領域に合わせて配置し、`alignmode = Outside(padding)` とします。
