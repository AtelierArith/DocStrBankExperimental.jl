```
G = largeRenv(renv[,label="Renv_",names=[label*"i" for i = 1:length(renv)],ext=".dmrjulia"])
```

環境 `renv` からハードディスクにテンソルを書き込み、`G` を通じて `names` で指定されたファイル名に従います（デフォルトのファイル拡張子: `.dmrjulia`）

参照: [`largeMPS`](@ref) [`largeMPO`](@ref) [`largeLenv`](@ref) [`largeEnv`](@ref)
