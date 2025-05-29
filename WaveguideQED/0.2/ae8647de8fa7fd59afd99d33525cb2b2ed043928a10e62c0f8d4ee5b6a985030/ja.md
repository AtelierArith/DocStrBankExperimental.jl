```
twophoton(b::WaveguideBasis{T,Nw},i::Int,ξ::Matrix;norm=false) where {T,Nw}
```

# 引数

  * `b::WaveguideBasis{T,Nw}` は複数の波導を含み、インデックス i が必要です。
  * `i` は二光子状態における波導のインデックスを示します: $\int_{t_0}^{t_{end}} dt' \int_{t_0}^{t_{end}} dt  \xi(t,t') w_{\mathrm{i}}^\dagger(t)w_{\mathrm{i}}^\dagger(t') |\emptyset \rangle$。
  * ξ は次元 `(b.nsteps, b.nsteps)` の行列として与えられます。
  * `norm::Bool=false`: 結果の波束を正規化するかどうかを切り替えます。
