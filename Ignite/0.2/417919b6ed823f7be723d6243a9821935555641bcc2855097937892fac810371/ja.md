```julia
once_filter(
    once::Union{Int64, AbstractVector{Int64}}
) -> Union{Ignite.OnceFilter{Int64}, Ignite.OnceFilter{T} where T<:AbstractVector{Int64}}

```

`FilteredEvent`で使用するイベントフィルタ関数を作成し、`once`に応じて特定のポイントで`true`を返します：

  * `once = n::Int`の場合、フィルタはイベントの`n`回目の発火時のみトリガーされます。
  * `once = Int[n₁, n₂, ...]`の場合、フィルタは`n₁`回目の発火、`n₂`回目の発火などでのみトリガーされます。
