```
G = largeLenv(Ns[,label="Lenv_",names=[label*"i" for i = 1:Ns],ext=".dmrjulia"])
```

ディスク上に大きな環境タイプを作成します（`Ns` テンソルを格納、要素タイプ: Float64）が、最初はディスクに何も書き込みません。`names` で指定されたファイル名（デフォルトのファイル拡張子: `.dmrjulia`）

参照: [`largeMPS`](@ref) [`largeMPO`](@ref) [`largeRenv`](@ref) [`largeEnv`](@ref)
