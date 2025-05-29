```
clear!(plan::RecoPlan{T}, preserve::Bool = true) where {T<:AbstractImageReconstructionParameters}
```

`plan`のすべてのプロパティをクリアします。`preserve`が`true`の場合、ネストされた`RecoPlan`は保持されます。
