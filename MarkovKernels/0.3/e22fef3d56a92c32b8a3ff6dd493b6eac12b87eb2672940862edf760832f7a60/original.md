invert(D::AbstractDistribution, K::AbstractMarkovKernel)

Computes a new distribution and Markov kernel such that

Dout(y) = ∫ K(y, x) D(x) dx, and Kout(x, y) = K(y, x) * D(x) / Dout(y)
