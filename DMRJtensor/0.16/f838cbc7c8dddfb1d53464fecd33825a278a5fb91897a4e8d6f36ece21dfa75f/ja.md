```
G = largeMPS(T,Ns[,label="mps_",names=[label*"i" for i = 1:length(psi)],ext=".dmrjulia"])
```

要素型 `T` の大きな MPS タイプを作成します（ディスクに保存されます）。`Ns` テンソルを持ちますが、最初は何もディスクに書き込みません。`names` で指定されたファイル名（デフォルトのファイル拡張子: `.dmrjulia`）

参照: [`largeMPO`](@ref) [`largeLenv`](@ref) [`largeRenv`](@ref) [`largeEnv`](@ref)
