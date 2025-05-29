```
G = largeRenv(T,Ns[,label="Renv_",names=[label*"i" for i = 1:Ns],ext=".dmrjulia"])
```

要素タイプ `T` の大きな環境タイプを作成し、`Ns` テンソルを持ちますが、最初はディスクに何も書き込みません。`names` で指定されたファイル名（デフォルトのファイル拡張子: `.dmrjulia`）

参照: [`largeMPS`](@ref) [`largeMPO`](@ref) [`largeLenv`](@ref) [`largeEnv`](@ref)
