```
apply!(
    r::ElemRestriction,
    u::CeedVector,
    ru::CeedVector;
    tmode=NOTRANSPOSE,
    request=RequestImmediate(),
)
```

[`ElemRestriction`](@ref) を使用して L ベクトルから E ベクトルに変換します（または転置操作を適用します）。入力 [`CeedVector`](@ref) は `u` で、結果は `ru` に格納されます。

`tmode` が `TRANSPOSE` の場合、結果は `ru` に加算されます。`tmode` が `NOTRANSPOSE` の場合、`ru` は結果で上書きされます。
