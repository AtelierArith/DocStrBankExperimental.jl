```
G,K = largeEnv(lenv,renv[,Llabel="Lenv_",Lnames=[label*"i" for i = 1:length(psi)],Rlabel="Renv_",Rnames=[label*"i" for i = 1:length(renv)],ext=".dmrjulia",type=Float64])
```

環境 `lenv` と `renv` からテンソルをハードディスクに書き込み、`G` と `K` を通じてそれぞれ取得され、`Lnames` と `Rnames` で指定されたファイル名に従います（デフォルトのファイル拡張子: `.dmrjulia`）

参照: [`largeMPS`](@ref) [`largeMPO`](@ref) [`largeLenv`](@ref) [`largeRenv`](@ref)
