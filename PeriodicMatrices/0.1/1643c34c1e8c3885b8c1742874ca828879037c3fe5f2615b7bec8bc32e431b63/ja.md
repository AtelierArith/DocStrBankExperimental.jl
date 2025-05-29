```
 hr2psm(Ahr::HarmonicArray, nrange) -> A::Matrix{Num}
```

ハーモニック配列 `Ahr` のハーモニック成分の範囲 `nrange` を記号行列 `A` に変換します。デフォルトの範囲は `nrange = 0:n` で、ここで `n` は最大ハーモニクスの次数です。  
