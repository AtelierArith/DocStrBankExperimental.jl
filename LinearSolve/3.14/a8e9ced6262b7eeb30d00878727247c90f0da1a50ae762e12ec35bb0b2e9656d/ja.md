```julia
MetalLUFactorization()
```

AppleのMetal GPUライブラリのラッパー。メモリの割り当てを避けるためにワークスペースを事前に割り当て、GPUに自動的にオフロードする方法でMetalに直接呼び出します。
