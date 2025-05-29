```
@P2G_Matrix grid=>(i,j) particles=>p mpvalues=>(ip,jp) [space] begin
    equations...
end
```

グローバル行列を組み立てるための粒子からグリッドへの転送マクロ。典型的なグローバル剛性行列は次のように組み立てることができます：

```julia
@P2G_Matrix grid=>(i,j) particles=>p mpvalues=>(ip,jp) begin
    K[i,j] = @∑ ∇w[ip] ⋅ c[p] ⋅ ∇w[jp] * V[p]
end
```

ここで `c` と `V` はそれぞれ剛性（対称四次）テンソルと体積を示します。グローバル剛性 `K` を作成するには [`create_sparse_matrix`](@ref) を使用することをお勧めします。
