```
ClipGrad(δ = 10)
ClipGrad(; [delta])
```

すべての勾配成分が `-δ ≤ dx[i] ≤ δ` を遵守するように制限します。

通常、[`OptimiserChain`](@ref)を使用して他のルールと組み合わせて構成されます。

他に[`ClipNorm`](@ref)も参照してください。
