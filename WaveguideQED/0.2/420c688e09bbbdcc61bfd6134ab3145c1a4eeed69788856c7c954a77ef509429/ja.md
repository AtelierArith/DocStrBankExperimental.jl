```
twophoton(b::WaveguideBasis{T,Nw},idx::I,ξ::Matrix;norm=false) where {T,Nw,I<:Union{Vector{Int64},Tuple{Vararg{Int64}}}}
```

# 引数

  * `b::WaveguideBasis{T,Nw}` は複数の波導を含み、インデックス i が必要です。
  * `I[1]` は二光子状態における波導のインデックス $i$ を示します: $\int_{t_0}^{t_{end}} dt' \int_{t_0}^{t_{end}} dt  \xi(t,t') w_{\mathrm{i}}^\dagger(t)w_{\mathrm{j}}^\dagger(t') |\emptyset \rangle$。
  * `I[2]` は二光子状態における波導のインデックス $j$ を示します: $\int_{t_0}^{t_{end}} dt' \int_{t_0}^{t_{end}} dt  \xi(t,t') w_{\mathrm{i}}^\dagger(t)w_{\mathrm{j}}^\dagger(t') |\emptyset \rangle$。
  * ξ は次元 `(b.nsteps, b.nsteps)` の行列として与えられます。
  * `norm::Bool=false`: 結果の波パケットを正規化するかどうかを切り替えます。
