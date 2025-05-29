```
conventionalize(v′::AbstractVec, cntr::Char)  -->  v::typeof(v′)
```

原始座標ベクトル `v′` を標準的な慣習基底（中心化タイプ `cntr` によって指定）に戻し、慣習的な座標ベクトル `v` を返します。

関連情報として [`primitivize`](@ref) と [`transform`](@ref) を参照してください。
