```
coefficient(a::GenericAffExpr{C,V}, v1::V, v2::V) where {C,V}
```

二次式 `a` における項 `v1 * v2` に関連付けられた係数を返します。

`coefficient(a, v1, v2)` は `coefficient(a, v2, v1)` と同じであることに注意してください。
