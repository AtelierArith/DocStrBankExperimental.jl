```julia
Routes{T} (Type Alias for Vector{T} where T <:AbstractRoute)
```

`Routes` は単純な一次元のルートのベクターです。複数のディスパッチを使用することで、これらのベクターは効果的にルーターとなり、複数のディスパッチを使用して拡張できます。個々の `Route` の機能を変更するには、`Route` と `MultiRoute` を参照してください。`Routes{T <: Any}` を `route!(c::AbstractConnection, r::Routes{T <: Any})` にディスパッチすると、新しいルーターが作成され、これはルートに対して `route!` を呼び出すことを意図しています。

```example

```

  * 参照: `AbstractConnection`, `Route`, `route`, `route!`
