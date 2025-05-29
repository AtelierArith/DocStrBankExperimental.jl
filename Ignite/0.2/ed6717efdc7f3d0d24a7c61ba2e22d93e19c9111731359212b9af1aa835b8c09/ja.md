```julia
timeout_filter(timeout::Real) -> Ignite.TimeoutFilter
timeout_filter(
    timeout::Real,
    start_time::Real
) -> Ignite.TimeoutFilter

```

`FilteredEvent`で使用するイベントフィルタ関数を作成します。この関数は、フィルタ関数が作成されてから少なくとも`timeout`秒が経過した場合に`true`を返します。
