```
TangentSpace{𝔽,M} = Fiber{𝔽,TangentSpaceType,M} where {𝔽,M<:AbstractManifold}
```

接点 $T_p\mathcal M$ の多様体で、点 $p\in\mathcal M$ におけるものです。これは、[`VectorSpaceFiber`](@ref) のエイリアスとしてモデル化され、[`TangentSpaceType`](@ref) に対応します。

# コンストラクタ

```
TangentSpace(M::AbstractManifold, p)
```

点 `p` における接空間 $T_p\mathcal M$ を表す多様体（ベクトル空間）を返します。$p\in\mathcal M$。
