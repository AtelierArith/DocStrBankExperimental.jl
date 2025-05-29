```
throttle(f::Function, args...; maxfps = 0.03)
```

`f(args...)` のアクションが最後に更新されてから `1/maxfps` の時間が経過した場合にのみ呼び出されるスロットルされた `Signal` を作成します。結果として得られる `Signal` は、1秒あたり最大 `maxfps` 回更新されます。
