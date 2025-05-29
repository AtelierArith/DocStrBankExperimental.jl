```julia
every_filter(
    every::Union{Int64, AbstractVector{Int64}}
) -> Union{Ignite.EveryFilter{Int64}, Ignite.EveryFilter{T} where T<:AbstractVector{Int64}}

```

`FilteredEvent`で使用するイベントフィルタ関数を作成し、`every`に応じて定期的に`true`を返します：

  * `every = n::Int`の場合、フィルタはイベントの毎`n`回目の発火でトリガーされます。
  * `every = Int[n₁, n₂, ...]`の場合、フィルタは毎`n₁`回目の発火、毎`n₂`回目の発火、などでトリガーされます。
