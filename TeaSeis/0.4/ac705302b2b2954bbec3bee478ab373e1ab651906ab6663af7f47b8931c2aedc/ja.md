```
readhdrs!(io, hdrs, smp_range, trace_range, range...)
```

JavaSeisファイルからデータのサブセット（ヘッダーのみ）をインプレースで読み込みます。パフォーマンスが重要な場合は、代わりに`readframehdrs!`の使用を検討してください。例:

# 3D:

```julia
readhdrs!(jsopen("data_3D.js"), hdrs, :, :, :)
readhdrs!(jsopen("data_3D.js"), hdrs, :, 1:2:end, 1:5)
```

# 4D:

```julia
readhdrs!(jsopen("data_4D.js"), hdrs, :, :, :, :)
readhdrs!(jsopen("data_4D.js"), hdrs, :, :, 2, 2:2:10)
```

# 5D:

```julia
readhdrs!(jsopen("data_5D.js"), hdrs, :, :, :, :, :)
readhdrs!(jsopen("data_5D.js"), hdrs, :, :, 2, 2:2:10, 1:10)
```
