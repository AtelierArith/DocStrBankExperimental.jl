```
corestrict(X, folds, i)
```

`X`（ベクトル、行列、またはテーブル）の制限で、`folds`は行インデックスのベクトルのタプルであり、`i`番目のフォールドの*補集合*に対して制限されます。

このメソッドはカリー化されているため、`corestrict(folds, i)`はデータに対して定義された演算子であり、`corestrict(folds, i)(X) = corestrict(X, folds, i)`となります。

### 例

```julia
folds = ([1, 2], [3, 4, 5],  [6,])
corestrict([:x1, :x2, :x3, :x4, :x5, :x6], folds, 2) # [:x1, :x2, :x6]
```
