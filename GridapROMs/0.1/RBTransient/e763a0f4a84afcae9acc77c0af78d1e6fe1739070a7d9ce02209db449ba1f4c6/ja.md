```
struct TransientReduction{A,B,RS<:Reduction{A,B},RT<:Reduction{A,EuclideanNorm}} <: Reduction{A,B}
  reduction_space::RS
  reduction_time::RT
end
```

一時的な問題における削減手法のラッパー。フィールド `reduction_space` と `reduction_time` はそれぞれ空間的削減手法と時間的削減手法を表します。
