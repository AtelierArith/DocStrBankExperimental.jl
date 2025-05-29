```julia
fdrand!(A, nx; ...)
fdrand!(A, nx, ny; ...)
fdrand!(A, nx, ny, nz; update, rand)

```

すべての非ゼロエントリをゼロに設定した後、単位ハイパーキューブ上の有限差分離散化データでそれぞれの更新行列を埋めます。パラメータのドキュメントについては[`fdrand`](@ref)を参照してください。

`size(A)==(N,N)`であることが必要で、ここで`N=nx*ny*nz`です。
