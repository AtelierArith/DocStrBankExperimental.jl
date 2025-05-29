```
fbp(plan, sino)
```

フィルタ付き逆投影 (FBP) 再構成。

# 入力

  * `plan::FBPplan`
  * `sino::AbstractArray{<:Number} (nb,na,...)` シノグラム

# 出力

  * `image::Matrix{<:Number} (nx,ny,...)` 再構成された画像
