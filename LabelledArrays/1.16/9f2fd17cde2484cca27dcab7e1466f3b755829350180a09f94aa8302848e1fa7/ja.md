```
LVector(v1::Union{SLArray,LArray}; kwargs...)
```

kwargsで置き換えられた対応するアイテムを持つv1のコピーを作成します。

例えば：

```
ABCD = @SLArray (2,2) (:a,:b,:c,:d);
B = ABCD(1,2,3,4);
B2 = LArray(B; c=30 )
```
