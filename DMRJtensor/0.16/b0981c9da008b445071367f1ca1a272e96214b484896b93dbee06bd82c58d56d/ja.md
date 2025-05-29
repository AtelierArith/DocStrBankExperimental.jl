```
G,K = largeEnv(T,Ns[,Llabel="Lenv_",Lnames=[label*"i" for i = 1:Ns],Rlabel="Renv_",Rnames=[label*"i" for i = 1:Ns],ext=".dmrjulia"])
```

`Ns`の型`T`のテンソルを持つ大きな環境を作成し、それぞれ`G`と`K`を通じて取得します。ファイル名は`Lnames`と`Rnames`で指定されます（デフォルトのファイル拡張子: `.dmrjulia`）

参照: [`largeMPS`](@ref) [`largeMPO`](@ref) [`largeLenv`](@ref) [`largeRenv`](@ref)
