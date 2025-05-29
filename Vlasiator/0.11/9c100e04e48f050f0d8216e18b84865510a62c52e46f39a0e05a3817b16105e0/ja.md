```
compute_flux_function(b::AbstractArray{T,N}, Δ::Vector{T}, nG::Int=2) where {T,N}
```

磁場 `b` と離散ステップ `Δ` から 2D 磁束関数 ψ を計算します。`nG` はベクトル場の各次元に沿ったゴーストセルの数です。ψ は $\psi = \int B_x dz = - \int B_z dx$ と定義され、$\mathbf{B} = \hat{y}\times\nabla\psi$ は X-Z 平面で、Y は面外方向です。これは B が発散のない場合と、導ガイド場 By が一定である場合に厳密に成り立ちます。しかし、数値的には誤差が生じます。現在の実装では、まず -z 境界に沿って積分し、その後 z に沿って進むことで ψ を計算します。参考文献: [Flux function](https://doi.org/10.1063/1.3657424)
