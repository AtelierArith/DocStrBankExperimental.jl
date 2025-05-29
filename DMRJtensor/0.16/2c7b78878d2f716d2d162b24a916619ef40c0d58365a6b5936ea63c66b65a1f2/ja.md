```
G = largeLenv(lenv[,label="Lenv_",names=[label*"i" for i = 1:length(lenv)],ext=".dmrjulia"])
```

環境 `lenv` からハードディスクにテンソルを書き込みます。これは `G` を通じて、`names` で指定されたファイル名に従って行われます（デフォルトのファイル拡張子: `.dmrjulia`）

参照: [`largeMPS`](@ref) [`largeMPO`](@ref) [`largeRenv`](@ref) [`largeEnv`](@ref)
