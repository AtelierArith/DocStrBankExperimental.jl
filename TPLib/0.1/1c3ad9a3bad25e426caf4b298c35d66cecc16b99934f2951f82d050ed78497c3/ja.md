```
compute_tropical_complex(M::Matrix{<:SemiRing}, n::Integer)
compute_tropical_complex(M::Matrix{<:Number}, n::Integer, semiring=:max)
```

トロピカルコーンに関連付けられたトロピカル複体を生成セットによって計算します。最小であり、すべてのベクトルが有限のエントリを持つ生成セットのみがサポートされています。戻り値はペア `(V::Matrix{<:Number},A::Vector{Vector{Int64}})` であり、`V` の行は複体の頂点であり、`A` は最大セルのコレクション（頂点との隣接によって定義される）です。各セルは通常の多面体として見なされ、トロピカルなものではなく、頂点は必ずしも一意ではないことに注意してください。

# 参考文献

[1] M. Develin and B. Sturmfels. Tropical convexity. Doc. Math., 9:1–27 (electronic), 2004. E-print arXiv:math.MG/0308254.
