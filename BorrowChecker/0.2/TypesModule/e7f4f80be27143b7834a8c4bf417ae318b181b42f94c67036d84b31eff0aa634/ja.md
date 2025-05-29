```
LazyAccessor{T,P,S,O<:Union{AbstractOwned,AbstractBorrowed}} <: AbstractWrapper{T}
```

所有または借用された値のプロパティまたはインデックスへの遅延アクセサです。コピーや移動を行わずにプロパティ/インデックスアクセスを可能にしながら、所有権のセマンティクスを維持します。

所有/借用された値のプロパティまたはインデックスにアクセスすると自動的に作成されます：

```julia
@own x = (a=1, b=2)
x.a  # LazyAccessorを返します
```

# 内部フィールド（公開APIの一部ではありません）：

  * `parent::P`: アクセスされている親値
  * `property::S`: アクセスされているプロパティ/インデックス
  * `property_type::Type{T}`: アクセスされているプロパティ/インデックスの型
  * `target::O`: 元の所有/借用された値
