```
twophoton(b::WaveguideBasis{T,Nw},i::Int,ξ::Function,args...;norm=false) where {T,Nw}
```

# 引数

  * `b::WaveguideBasis{T,Nw}` は複数の波導を含み、インデックス i が必要です。
  * `i` は二光子状態における波導のインデックスを示します: $\int_{t_0}^{t_{end}} dt' \int_{t_0}^{t_{end}} dt  \xi(t,t') w_{\mathrm{i}}^\dagger(t)w_{\mathrm{i}}^\dagger(t') |\emptyset \rangle$。
  * 関数として与えられた ξ は `ξ(t1,t2,args...)` の形式に従う必要があり、`t1` と `t2` は入力時間です。
  * `args...`: ξ に渡される追加の引数。
  * `norm::Bool=false`: 結果の波束を正規化するかどうかを切り替えます。
