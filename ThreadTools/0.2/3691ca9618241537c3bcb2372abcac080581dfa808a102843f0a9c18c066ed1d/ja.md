```
tmap(f, args...)
tmap(f, v, T::DataType)
tmap(f, nthreads::Int, args...)
tmap1(f, args...)
tmap1(f, nthreads::Int, args...)
```

スレッドマップ。オプションの引数 `nthreads` は、並列で使用されるスレッドの数を制限します。`tmap1` は `tmap` と同じですが、julia がスレッドに1つしかアクセスできない場合は通常の `map` にフォールバックします。出力のエルタイプ `T` が指定されている場合、呼び出しは型安定になります。
