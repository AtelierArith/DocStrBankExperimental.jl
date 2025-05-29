```
brightness(::AbstractMatrix{T}) -> AbstractMatrix{Float64}
```

与给定的颜色三通道`画像`，求出其亮度并以`浮点数`的形式输出

# 注意

由于实验中记录的全息图都是灰度图像，其三个通道分量颜色都是一致的，故取某一颜色分量作为其亮度即可
