```
ScaledVectorTransport{T} <: AbstractVectorTransportMethod
```

任意の [`AbstractVectorTransportMethod`](@ref) `T` のスケーリングされたバリアントを導入します。これは、[SatoIwai:2013](@cite) で導入されたもので、ある $X∈ T_p\mathcal M$ に対して次のように定義されます。

$$
    \mathcal T^{\mathrm{S}}(X) = \frac{\lVert X\rVert_p}{\lVert \mathcal T(X)\rVert_q}\mathcal T(X).
$$

結果として得られる点 `q` は知られている必要があります。すなわち、[`vector_transport_direction`](@ref) の場合、曲線、あるいはより正確にはその終点が知られている必要があります（指数写像またはリトラクションを介して）。したがって、[`vector_transport_to`](@ref) に対してのみデフォルトの実装が提供されています。

# コンストラクタ

```
ScaledVectorTransport(m::AbstractVectorTransportMethod)
```
