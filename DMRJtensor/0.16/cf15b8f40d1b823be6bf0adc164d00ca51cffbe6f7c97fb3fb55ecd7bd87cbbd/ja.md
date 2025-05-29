```
G,K = largeEnv(Ns[,Llabel="Lenv_",Lnames=[label*"i" for i = 1:Ns],Rlabel="Renv_",Rnames=[label*"i" for i = 1:Ns],ext=".dmrjulia",type=Float64])
```

`Ns` テンソルを持つ大きな環境を作成し、`Lnames` と `Rnames` で指定されたファイル名に従ってそれぞれ `G` と `K` を通じて取得します（デフォルトのファイル拡張子: `.dmrjulia`）

参照: [`largeMPS`](@ref) [`largeMPO`](@ref) [`largeLenv`](@ref) [`largeRenv`](@ref)
