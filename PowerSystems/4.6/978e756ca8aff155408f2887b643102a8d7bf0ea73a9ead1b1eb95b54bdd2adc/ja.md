```julia
transform_single_time_series!(
    sys::PowerSystems.System,
    horizon::Dates.Period,
    interval::Dates.Period;
    resolution
)

```

`System`内のすべての[`SingleTimeSeries`](@ref)のインスタンスを[`DeterministicSingleTimeSeries`](@ref)に変換します。

これは、実際の予測が利用できない場合に、歴史的な測定値や実現から完璧な予測を生成するために使用でき、データを不必要に重複させることはありません。

すべての`SingleTimeSeries`インスタンスを変換できない場合は、どれも変換されません。

既存の`DeterministicSingleTimeSeries`予測は、入力が無効であっても削除されます。

# 引数

  * `sys::System`: コンポーネントを含むシステム。
  * `horizon::Dates.Period`: 各予測[ウィンドウ](@ref W)の希望する[horizon](@ref H)
  * `interval::Dates.Period`: 予測[ウィンドウ](@ref W)間の希望する[間隔](@ref I)
  * `resolution::Union{Nothing, Dates.Period} = nothing`: 設定されている場合、この解像度を持つ時系列のみを変換します。
