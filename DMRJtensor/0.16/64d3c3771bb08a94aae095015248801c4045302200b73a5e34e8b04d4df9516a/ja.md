```
G = largeMPO(Ns[,label="mpo_",names=[label*"i" for i = 1:length(mpo)],ext=".dmrjulia"])
```

ディスク上に大きなMPOタイプを作成します（`Ns`テンソルを使用、要素タイプ：Float64）ですが、最初はディスクに何も書き込みません。`names`で指定されたファイル名（デフォルトのファイル拡張子：`.dmrjulia`）

参照：[`largeMPS`](@ref) [`largeLenv`](@ref) [`largeRenv`](@ref) [`largeEnv`](@ref)
