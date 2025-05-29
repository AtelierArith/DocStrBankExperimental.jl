sdm(     holo::AbstractMatrix{T},      windows_size::Tuple{Integer,Integer},      interval::Tuple{Integer,Integer},      P::FFTW.FFTWPlan,      scale::Integer;      shift = false     ) -> AbstractMatrix where T <: AbstractFloat

`空域掩膜法`的算法实现，具体可见`doi: 10.1109/JDT.2015.2479646`

# Arguments

  * holo: 全息图（非RGB类型而是AbstractFloat类型）
  * windows_size: 掩膜窗口大小
  * interval: 窗口偏移量
  * holo: 原始全息图
  * P: 其类型为FFTW.FFTWPlan，表示重建采用`fft`傅立叶变换
  * scale: 由于零级像强度过大，故需要用`scale`拉升±1级像的强度
  * shift: 是否旋转图像，默认为否（除非是想展示完整的重建像，否则不建议将`shift`设为`true`，因为其内存和时间开销比较大）
