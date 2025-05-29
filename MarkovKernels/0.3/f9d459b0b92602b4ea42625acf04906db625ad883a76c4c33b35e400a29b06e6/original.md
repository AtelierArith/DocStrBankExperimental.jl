```
htransform(K::AbstractMarkov, L::AbstractLikelihood)
```

Computes a Markov kernel Kout and Likelihood Lout such that

Lout(z) = ∫ L(x) K(x, z) dx, and Kout(x, z) = L(x) K(x, z) / Lout(z)
