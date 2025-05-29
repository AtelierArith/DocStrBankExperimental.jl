```
timeseries(x::Observable{{Union{Number, Point2}}})
```

サンプリングされた信号をプロットします。使用法：

```julia
signal = Observable(1.0)
scene = timeseries(signal)
display(scene)
# @asyncはオプションですが、より多くのコードの評価を続けるのに役立ちます
@async while isopen(scene)
    # 例えばセンサーからデータを取得：
    data = rand()
    # 信号を更新
    signal[] = data
    # 新しいデータを待つ/何かをする...
    # ここでyieldすることが重要ですが、そうしないと何もレンダリングされません
    sleep(1/30)
end

```
