```julia
begin_time_series_update(
    func::Function,
    sys::PowerSystems.System
) -> Any

```

時系列の更新を開始します。パフォーマンスを向上させるために、多くの時系列配列を追加する際にこの関数を使用します。

更新中にエラーが発生した場合、変更は元に戻されます。

現在、この関数を使用して時系列を削除することはサポートされていません。

# 例

```julia
begin_time_series_update(sys) do
    add_time_series!(sys, component1, time_series1)
    add_time_series!(sys, component2, time_series2)
end
```
