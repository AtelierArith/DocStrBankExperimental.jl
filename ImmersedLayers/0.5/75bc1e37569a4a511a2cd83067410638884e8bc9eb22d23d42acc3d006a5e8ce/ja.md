```
normal_interpolate_symm!(τ::VectorData,A::EdgeGradient{Primal},cache::BasicILMCache)
normal_interpolate_symm!(τ::VectorData,A::EdgeGradient{Primal},sys::ILMSystem)
```

操作 $\mathbf{\tau} = \mathbf{n} \cdot R_t^T (\mathbf{A} +\mathbf{A}^T - (\mathrm{tr}\mathbf{A})\mathbf{I})$ は、グリッドテンソルデータ `A`（速度勾配テンソルのような）をベクトル表面データ `τ`（トラクションのような）にマッピングします。これは [`regularize_normal_symm!`](@ref) の随伴です。
