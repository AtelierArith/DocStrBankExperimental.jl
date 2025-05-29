```julia
route!(c::AbstractConnection, vec::Routes, r::AbstractMultiRoute) -> ::Nothing
```

この `route!` ディスパッチは、`route!` ベースのルーターの下に別のルーターが存在することを許可します。この `Function` は、マルチルートがルーティングされるたびに呼び出されます。これは **インポート** され、拡張されるように設計されています。これを行うには、まず `MultiRoute` に基づいて独自の `<:AbstractMultiRoute` を作成し、その型のためにこの `Method` を記述します。例えば、デフォルトの `Toolips.MultiRoute` は、受信する `Connection` のタイプに応じて `Route{<:AbstractConnection}` をルーティングします。

  * 参照: `Route`, `Routes`, `Connection`, `AbstractConnection`, `MultiRoute`
