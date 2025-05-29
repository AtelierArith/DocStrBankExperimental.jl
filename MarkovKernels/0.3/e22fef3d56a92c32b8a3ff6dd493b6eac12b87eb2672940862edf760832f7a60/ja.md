invert(D::AbstractDistribution, K::AbstractMarkovKernel)

新しい分布とマルコフカーネルを計算します。

Dout(y) = ∫ K(y, x) D(x) dx, および Kout(x, y) = K(y, x) * D(x) / Dout(y)
