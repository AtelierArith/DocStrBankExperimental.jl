```
baltrunc_unstab(sys::LTISystem; residual = false, n = missing, kwargs...)
```

不安定モデルのためのバランス切り捨て。`sys = sys_stable + sys_unstable` への加法分解が行われ、その後 `sys_stable` が削減されます。順序 `n` は不安定な極の数未満であってはなりません。

他のキーワード引数については `baltrunc2` を参照してください。
