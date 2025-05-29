```
Toeplitz(vc::AbstractVector, vr::AbstractVector)
```

最初の列 `vc` と最初の行 `vr` から `Toeplitz` 行列を作成します。ただし、`vc[1] == vr[1]` である必要があります。
