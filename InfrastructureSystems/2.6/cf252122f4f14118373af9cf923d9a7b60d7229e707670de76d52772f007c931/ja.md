```julia
get_time_series_multiple(
    owner::Union{InfrastructureSystems.InfrastructureSystemsComponent, InfrastructureSystems.SupplementalAttribute};
    ...
) -> Union{Tuple{}, Channel{Any}}
get_time_series_multiple(
    owner::Union{InfrastructureSystems.InfrastructureSystemsComponent, InfrastructureSystems.SupplementalAttribute},
    filter_func;
    type,
    name,
    resolution
) -> Union{Tuple{}, Channel{Any}}

```

コンポーネントまたは属性に関連付けられた TimeSeriesData インスタンスのイテレータを返します。

フィルタ関数を渡すと、メディアから時系列データを読み取るため、他のフィルタリングパラメータよりも遅くなる可能性があることに注意してください。

結果に対して `collect` を呼び出すと、配列を取得できます。

# 引数

  * `owner::TimeSeriesOwners`: 時系列を取得するコンポーネントまたは属性
  * `filter_func = nothing`: これが true を返す時系列のみを返します。
  * `type::Union{Nothing, ::Type{<:TimeSeriesData}} = nothing`: このタイプの時系列のみを返します。
  * `name::Union{Nothing, AbstractString} = nothing`: この値に一致する時系列のみを返します。
  * `resolution::Union{Nothing, Dates.Period} = nothing`: この値に一致する時系列のみを返します。

参照: [`get_time_series_multiple` from a `System`](@ref get_time_series_multiple(     data::SystemData,     filter_func = nothing;     type = nothing,     name = nothing, ))
