```
permute_systems(X::AbstractMatrix, perm::Vector, dims::Matrix)
```

行列 `X` のサブシステムの順序を、置換 `perm` に従って、次元 `dims` で構成されたサブシステムに基づいて置換します。 `dims` は n × 2 の行列であり、`dims[i, 1]` はサブシステム i の行数、`dims[i, 2]` はその列数です。
