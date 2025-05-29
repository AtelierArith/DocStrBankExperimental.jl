```
G = largeMPO(T,Ns[,label="mpo_",names=[label*"i" for i = 1:length(mpo)],ext=".dmrjulia"])
```

要素タイプ `T` の大きな MPO タイプを作成し、`Ns` テンソルを持ちますが、最初はディスクに何も書き込みません。`names` で指定されたファイル名（デフォルトのファイル拡張子: `.dmrjulia`）

参照: [`largeMPS`](@ref) [`largeLenv`](@ref) [`largeRenv`](@ref) [`largeEnv`](@ref)
