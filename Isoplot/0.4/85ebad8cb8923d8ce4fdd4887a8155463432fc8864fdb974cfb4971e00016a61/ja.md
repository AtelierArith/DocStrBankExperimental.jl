```julia
UPbAnalysis(r²⁰⁷Pb²³⁵U, σ²⁰⁷Pb²³⁵U, r²⁰⁶Pb²³⁸U, σ²⁰⁶Pb²³⁸U, correlation; T=Float64)
```

個々の同位体比と（1シグマ！）不確実性から `UPbAnalysis` オブジェクトを構築します。

### 例

```
julia> UPbAnalysis(22.6602, 0.0175, 0.40864, 0.00017, 0.83183)
UPbAnalysis{Float64}([22.6602, 0.40864], [0.00030625000000000004 2.4746942500000003e-6; 2.4746942500000003e-6 2.8900000000000004e-8])
```
