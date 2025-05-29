```julia
reversecopyat!(dest, src, tₛ::AbstractVector{Bool})
```

`copyat!`と同様ですが、格納された要素の順序も逆にします。

`dest .= reverse(src[tₛ])`と同等ですが、アロケーションを引き起こすことはありません。
