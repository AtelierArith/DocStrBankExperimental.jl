```
G = largeMPO(mpo[,label="mpo_",names=[label*"i" for i = 1:length(mpo)],ext=".dmrjulia"])
```

`mpo` から取得された `MPO` のテンソルを、`names` で指定されたファイル名に従ってハードディスクに書き込みます（デフォルトのファイル拡張子: `.dmrjulia`）

参照: [`largeMPS`](@ref) [`largeLenv`](@ref) [`largeRenv`](@ref) [`largeEnv`](@ref)
