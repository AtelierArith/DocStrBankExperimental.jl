```
reconst(holo::AbstractMatrix, P::FFTW.FFTWPlan, scale::Integer; shift=false) -> AbstractMatrix
```

对无透镜傅立叶全息图进行数值重建

# Arguments

  * `holo`: 无透镜傅立叶全息图
  * `P`: 其类型为FFTW.FFTWPlan，表示重建采用`fft`傅立叶变换
  * `scale`: 由于零级像强度过大，故需要用`scale`拉升±1级像的强度
  * `shift`: 是否旋转图像，默认为否（除非是想展示完整的重建像，否则不建议将`shift`设为`true`，因为其内存和时间开销比较大）
  * `nthreads`: 是否开启多线程，默认为是（值得注意的是，该线程与傅立叶变换多线程的开启无关）
