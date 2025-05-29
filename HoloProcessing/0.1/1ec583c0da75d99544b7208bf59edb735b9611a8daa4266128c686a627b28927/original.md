```
ldr(
    holo::AbstractMatrix{T}, 
    N::Integer, 
    interval::Tuple{Integer,Integer}, 
    P::FFTW.FFTWPlan, 
    scale::Integer; 
    shift = false
    ) -> AbstractMatrix{T} where T <: AbstractFloat
```

`低维度重建法`的算法实现，具体可见`doi: 10.1364/AO.414773`

# Arguments

  * holo: 全息图
  * N: 窗口大小的`N`倍就等于`holo`的大小
  * interval: 窗口偏移量
  * holo: 原始全息图
  * P: 其类型为FFTW.FFTWPlan，表示重建采用`fft`傅立叶变换
  * scale: 由于零级像强度过大，故需要用`scale`拉升±1级像的强度
  * shift: 是否旋转图像，默认为否（除非是想展示完整的重建像，否则不建议将`shift`设为`true`，因为其内存和时间开销比较大）
