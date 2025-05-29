```
G = largeMPS(psi[,label="mps_",names=[label*"i" for i = 1:length(psi)],ext=".dmrjulia"])
```

`MPS` `psi` から `G` を通じて取得されたテンソルを、`names` で指定されたファイル名に従ってハードディスクに書き込みます（デフォルトのファイル拡張子: `.dmrjulia`）

参照: [`largeMPO`](@ref) [`largeLenv`](@ref) [`largeRenv`](@ref) [`largeEnv`](@ref)
