```
normal_interpolate!(τ::VectorData,A::EdgeGradient{Primal},cache::BasicILMCache)
normal_interpolate!(τ::VectorData,A::EdgeGradient{Primal},sys::ILMSystem)
```

操作 $\mathbf{\tau} = \mathbf{n} \cdot R_t^T \mathbf{A}$ は、グリッドテンソルデータ `A`（速度勾配テンソルのような）をベクトル表面データ `τ`（牽引のような）にマッピングします。これは [`regularize_normal!`](@ref) の随伴です。
