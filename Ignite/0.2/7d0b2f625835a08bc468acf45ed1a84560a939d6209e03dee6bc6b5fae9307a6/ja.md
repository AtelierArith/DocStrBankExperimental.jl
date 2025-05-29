```julia
throttle_filter(throttle::Real) -> Ignite.ThrottleFilter
throttle_filter(
    throttle::Real,
    last_fire::Real
) -> Ignite.ThrottleFilter

```

`FilteredEvent`で使用するイベントフィルタ関数を作成します。これは、最後に発火してから少なくとも`throttle`秒が経過した場合に`true`を返します。
