# 拡張ヘルプ

```
volume(am::AbstractAffineMap)
```

### 注意事項

この実装は、次元を保持するマップ（すなわち、正方行列）を必要とします。

### アルゴリズム

正方線形マップは、任意の集合の体積をその絶対行列式でスケーリングします。平行移動は体積に影響を与えません。したがって、`M * X + {v}` の体積は `|det(M)| * volume(X)` です。
