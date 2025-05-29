```
spec(name::Symbol)::GroupSpec
```

提供された標準的なグループ仕様の `name` からグループ仕様を取得します。これはライブラリにハードコーディングされています。

# 例

```julia
# NIST 楕円曲線 P-192 仕様:
p192_spec = spec(:P_192)
P192 = concretize_type(ECGroup, p192_spec)

# モジュラープライムグループ仕様
modp_spec = spec(:RFC5114_2048_224)
MODP = concretize_type(PGroup, modp_spec)
```

`concretize_type`、`@ECGroup`、`@PGroup` も参照してください。
