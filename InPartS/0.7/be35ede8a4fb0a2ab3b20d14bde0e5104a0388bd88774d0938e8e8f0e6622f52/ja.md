```
AbstractRegistrar{T}
```

レジストラのための抽象型。サブタイプ `XxxxRegistrar{T}` は次の関数を実装する必要があります。

```julia
get_id!(reg::XxxxRegistrar{T}, parent::T, sim::Simulation, futureparticle::AbstractParticle) → T
```

この関数は、呼び出すたびにタイプ `T` の（できればユニークな）識別子を返します。`T` を返すヘルパー関数 [`_idtype`](@ref) が付属しています。
