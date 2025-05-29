```
readtrcs(io, sample_range, trace_range, range...)
```

JavaSeisファイルからデータのサブセット（トレースのみ）をアウトオブプレースで読み取ります。トレースデータの配列を返します。パフォーマンスが重要な場合は、代わりに`readframetrcs`を使用することを検討してください。例：

# 3D:

```julia
trcs = readtrcs(jsopen("data_3D.js"), :, :, :)
trcs = readtrcs(jsopen("data_3D.js"), :, 1:2:end, 1:5)
```

# 4D:

```julia
trcs = readtrcs(jsopen("data_4D.js"), :, :, :, :)
trcs = readtrcs(jsopen("data_4D.js"), :, :, 2, 2:2:10)
```

# 5D:

```julia
trcs = readtrcs(jsopen("data_5D.js"), :, :, :, :, :)
trcs = readtrcs(jsopen("data_5D.js"), :, :, 2, 2:2:10, 1:10)
```
