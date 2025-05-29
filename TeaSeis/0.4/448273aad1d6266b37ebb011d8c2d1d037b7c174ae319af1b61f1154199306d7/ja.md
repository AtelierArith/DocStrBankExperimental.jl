```
readtrcs!(io, trcs, sample_range, trace_range, range...)
```

JavaSeisファイルからデータのサブセット（トレースのみ）をインプレースで読み込みます。パフォーマンスが重要な場合は、代わりに`readframetrcs!`の使用を検討してください。例：

# 3D:

```julia
readtrcs!(jsopen("data_3D.js"), trcs, :, :, :)
readtrcs!(jsopen("data_3D.js"), trcs, :, 1:2:end, 1:5)
```

# 4D:

```julia
readtrcs!(jsopen("data_4D.js"), trcs, :, :, :, :)
readtrcs!(jsopen("data_4D.js"), trcs, :, :, 2, 2:2:10)
```

# 5D:

```julia
readtrcs!(jsopen("data_5D.js"), trcs, :, :, :, :, :)
readtrcs!(jsopen("data_5D.js"), trcs, :, :, 2, 2:2:10, 1:10)
```
