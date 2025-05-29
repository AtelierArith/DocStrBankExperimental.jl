```
normalizek(krs::AbstractVector{<:KRatios}; norm::Float32=1.0f)::Vector{KRatios}
normalizek(krs::AbstractVector{KRatio}; norm::Float32=1.0f)::Vector{KRatio}
```

KRatiosデータ配列の各ポイントに対して、ピクセルごとの正規化k比を計算します。`norm`は1.0以外の正規化定数を指定します。
