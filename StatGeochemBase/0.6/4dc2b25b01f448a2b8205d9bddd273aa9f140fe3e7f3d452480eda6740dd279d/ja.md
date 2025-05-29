```julia
copyat!(dest, src, tₛ::AbstractVector{Bool})
```

tₛがtrueのときにsrcからdestにコピーします。`dest .= src[tₛ]`と同等ですが、アロケーションを引き起こしません。

関連: `reversecopyat!`
