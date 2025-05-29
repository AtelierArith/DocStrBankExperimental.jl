```
G = largeMPS(Ns[,label="mps_",names=[label*"i" for i = 1:length(psi)],ext=".dmrjulia"])
```

ディスク上に大きなMPSタイプを作成します（`Ns`テンソル、要素タイプ：Float64）ですが、最初はディスクに何も書き込みません。`names`で指定されたファイル名（デフォルトのファイル拡張子：`.dmrjulia`）

参照：[`largeMPO`](@ref) [`largeLenv`](@ref) [`largeRenv`](@ref) [`largeEnv`](@ref)
