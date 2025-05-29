```
modes(a, [r])::Vector
mode(a::AbstractArray, wv::AbstractWeights)::Vector
```

配列のすべてのモード（最も一般的な数値）を返します。オプションで、指定された範囲 `r` にわたって、またはベクトル `wv` を介して重み付けされます。
