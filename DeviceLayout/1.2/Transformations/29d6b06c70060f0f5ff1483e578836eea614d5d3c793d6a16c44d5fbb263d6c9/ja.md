```
struct ScaledIsometry{T<:Union{Point, Nothing}} <: AbstractAffineMap
ScaledIsometry(origin=nothing, rotation=0°, xrefl=false, mag=1.0)
```

角度を保持する座標変換。

`f::ScaledIsometry`の同等の変換は、次の変換の合成であり、反射が最初に適用される順序で行われます：

1. `xrefl(f)`が`true`の場合、`x`軸に沿った反射
2. `rotation(f)`による回転
3. `mag(f)`による拡大
4. `origin(f)`による平行移動

次のようにも構築できます：

```julia
ScaledIsometry(f::Transformation) = ScaledIsometry(origin(f), rotation(f), xrefl(f), mag(f))
```

ただし、`f`がスケール不変（角度を保持しない）でない場合、`DomainError`がスローされます。

`ScaledIsometry`を含む`Transformation`の合成（`compose`または`∘`を使用）では、他の変換も角度を保持する場合、`ScaledIsometry`が返されます。
