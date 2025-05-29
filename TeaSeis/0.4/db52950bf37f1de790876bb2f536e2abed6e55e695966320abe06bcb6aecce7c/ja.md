```
readhdrs(io, trace_range, range...)
```

JavaSeisファイルからデータのサブセット（ヘッダーのみ）をアウトオブプレースで読み取ります。トレースデータの配列を返します。パフォーマンスが重要な場合は、代わりに`readframetrcs`の使用を検討してください。例：

# 3D:

```julia
hdrs = readhdrs(jsopen("data_3D.js"), :, :, :)
hdrs = readhdrs(jsopen("data_3D.js"), :, 1:2:end, 1:5)
```

# 4D:

```julia
hdrs = readhdrs(jsopen("data_4D.js"), :, :, :, :)
hdrs = readhdrs(jsopen("data_4D.js"), :, :, 2, 2:2:10)
```

# 5D:

```julia
hdrs = readhdrs(jsopen("data_5D.js"), :, :, :, :, :)
hdrs = readhdrs(jsopen("data_5D.js"), :, :, 2, 2:2:10, 1:10)
```
