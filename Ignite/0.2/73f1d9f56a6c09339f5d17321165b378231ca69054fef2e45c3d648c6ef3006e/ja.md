入力 `event` を条件付きで発火させるためにフィルタリングします：

入力：

  * `event::AbstractFiringEvent`: フィルタリングされるイベント。
  * `event_filter::Any`: フィルタリングされたイベントが発火すべきかどうかを返すイベントフィルタ関数 `(::Engine, ::AbstractFiringEvent) -> Bool`。
  * `every::Union{Int, <:AbstractVector{Int}}`: フィルタリングされたイベントが発火すべき期間； [`every_filter`](@ref) を参照してください。
  * `once::Union{Int, <:AbstractVector{Int}}`: フィルタリングされたイベントが発火すべきポイント； [`once_filter`](@ref) を参照してください。
