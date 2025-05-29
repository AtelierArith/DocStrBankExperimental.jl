```
maximise(f, X, structure = SortedVector, tol=1e-3)
または
maximise(f, X, structure = HeapedVector, tol=1e-3)
または
maximise(f, X, tol=1e-3) この場合、"structure" のデフォルト値は "HeapedVector" です
```

関数 `f` のグローバル最大値を `Interval` または `IntervalBox` `X` 上でモーア-スケルボーアルゴリズムを使用して見つけます。利用可能なオプションの説明については [`minimise`](@ref) を参照してください。
��
