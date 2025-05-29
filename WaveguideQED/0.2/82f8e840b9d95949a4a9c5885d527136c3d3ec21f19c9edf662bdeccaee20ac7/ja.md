```
twophoton(b::WaveguideBasis{T,Nw},idx::I,ξ::Function,times,args...;norm=false) where {T,Nw,I<:Union{Vector{Int64},Tuple{Vararg{Int64}}}} = twophoton(b,idx[1],idx[2],ξ,times,args...,norm=norm)
```

# 引数

  * `b::WaveguideBasis{T,Nw}` は複数の波導を含み、インデックス i が必要です。
  * `I[1]` は二光子状態における波導のインデックス $i$ を示します: $\int_{t_0}^{t_{end}} dt' \int_{t_0}^{t_{end}} dt  \xi(t,t') w_{\mathrm{i}}^\dagger(t)w_{\mathrm{j}}^\dagger(t') |\emptyset \rangle$。
  * `I[2]` は二光子状態における波導のインデックス $j$ を示します: $\int_{t_0}^{t_{end}} dt' \int_{t_0}^{t_{end}} dt  \xi(t,t') w_{\mathrm{i}}^\dagger(t)w_{\mathrm{j}}^\dagger(t') |\emptyset \rangle$。
  * 関数として与えられた ξ は `ξ(times[l],times[m],args...)` に従う必要があります。
  * `times`: 長さ(length(times)) = b.nsteps のベクトルまたは範囲。
  * `args...`: ξ に渡される追加の引数。
  * `norm::Bool=false`: 結果の波束を正規化するかどうかを切り替えます。
