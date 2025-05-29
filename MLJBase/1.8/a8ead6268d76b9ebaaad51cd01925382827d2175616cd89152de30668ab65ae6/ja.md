```
restrict(X, folds, i)
```

`X`の制限、ベクトル、行列、またはテーブルを`folds`の`i`番目のフォールドに、ここで`folds`は行インデックスのベクトルのタプルです。

このメソッドはカリー化されているため、`restrict(folds, i)`はデータに対して定義された演算子であり、`restrict(folds, i)(X) = restrict(X, folds, i)`となります。

### 例

# 

```julia
folds = ([1, 2], [3, 4, 5],  [6,])
restrict([:x1, :x2, :x3, :x4, :x5, :x6], folds, 2) # [:x3, :x4, :x5]
```

参照してください [`corestrict`](@ref)
