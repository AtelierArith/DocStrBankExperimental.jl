```
timeseries(x::Node{{Union{Number, Point2}}})
```

サンプリングされた信号をプロットします。使用法：

```julia
signal = Node(1.0)
scene = timeseries(signal)
display(scene)
# @asyncはオプションですが、より多くのコードを評価し続けるのに役立ちます
@async while isopen(scene)
    # 例えばセンサーからデータを取得：
    data = rand()
    # 信号を更新
    signal[] = data
    # 新しいデータを待つ/何でも...
    # ここでイールドすることが重要ですが、そうしないと何もレンダリングされません
    sleep(1/30)
end

```
