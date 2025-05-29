```julia
open_time_series_store!(
    func::Function,
    sys::PowerSystems.System;
    ...
) -> Any
open_time_series_store!(
    func::Function,
    sys::PowerSystems.System,
    mode,
    args...;
    kwargs...
) -> Any

```

バルク追加または読み取りのために時系列ストアを開きます

これは、HDF5ファイルを開閉する際のオーバーヘッドのため、`add_time_series!`を何度も呼び出す前に推奨されます。

メモリ内の時系列ストアには必要ありません。

# 例

```julia
# コンポーネントの配列とSingleTimeSeriesがそれぞれcomponentsとsingle_time_seriesという変数に格納されているシステムがあると仮定します
open_time_series_store!(sys, "r+") do
    for (component, ts) in zip(components, single_time_series)
        add_time_series!(sys, component, ts)
    end
end
```

この関数を使用して読み取りを高速化することもできます。モードを`"r+"`から`"r"`に変更して、ファイルを読み取り専用で開きます。

関連情報: [`begin_time_series_update`](@ref)
