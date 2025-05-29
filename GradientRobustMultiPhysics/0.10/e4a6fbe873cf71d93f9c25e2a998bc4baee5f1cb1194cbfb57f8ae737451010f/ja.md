```
function CombineDofs(idX::Int,idY::Int,dofsX::Array{Int,1},dofsY::Array{Int,1})
```

は、CombineDofs 制約を構築します。これは（PDEDescription に割り当てられた場合）、id idX の未知数の dofsX が id idY の未知数の dofsY と一致することを保証します。
