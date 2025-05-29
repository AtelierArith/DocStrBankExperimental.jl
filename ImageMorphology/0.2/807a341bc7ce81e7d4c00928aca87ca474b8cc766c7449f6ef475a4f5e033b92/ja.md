```
thinning(img::AbstractArray{Bool}; algo::ThinAlgo=GuoAlgo())
```

入力画像のスケルトン化を達成するために、バイナリブロブの細化操作を適用します。

参照: [`GuoAlgo`](@ref)
