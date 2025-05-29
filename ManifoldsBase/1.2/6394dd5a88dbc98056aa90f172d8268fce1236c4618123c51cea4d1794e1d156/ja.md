```
CotangentSpace{𝔽,M} = Fiber{𝔽,CotangentSpaceType,M} where {𝔽,M<:AbstractManifold}
```

点 $p\in\mathcal M$ における余接空間 $T^*_p\mathcal M$ の多様体。これは [`VectorSpaceFiber`](@ref) のエイリアスとしてモデル化され、[`CotangentSpaceType`](@ref) に対応します。

# コンストラクタ

```
CotangentSpace(M::AbstractManifold, p)
```

点 `p` における余接空間 $T^*_p\mathcal M$ を表す多様体（ベクトル空間）を返します。$p\in\mathcal M$。
