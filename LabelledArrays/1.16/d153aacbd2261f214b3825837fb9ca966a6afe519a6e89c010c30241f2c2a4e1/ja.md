```
SLVector(v1::SLArray; kwargs...)
```

v1のコピーを作成し、kwargs内の対応する項目を置き換えます。

例えば：

```
ABCD = @SLArray (2,2) (:a,:b,:c,:d);
B = ABCD(1,2,3,4);
B2 = SLArray(B; c=30 )
```
