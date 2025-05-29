```
CachedBasis{𝔽,V,<:AbstractBasis{𝔽}} <: AbstractBasis{𝔽}
```

与えられた `basis` のキャッシュされたバージョンで、事前に計算された基底ベクトルを持っています。基底ベクトルは `data` に格納されており、明示的に（[`ProjectedOrthonormalBasis`](@ref) のキャッシュされたバリアントのように）または暗黙的に格納されています。

# コンストラクタ

```
CachedBasis(basis::AbstractBasis, data)
```
