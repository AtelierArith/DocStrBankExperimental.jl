```
Roots.A42()
```

Bracketing method which finds the root of a continuous function within a provided bracketing interval `[a, b]`, without requiring derivatives. It is based on Algorithm 4.2 described in: G. E. Alefeld, F. A. Potra, and Y. Shi, "Algorithm 748: enclosing zeros of continuous functions," ACM Trans. Math. Softw. 21, 327–344 (1995), DOI: [10.1145/210089.210111](https://doi.org/10.1145/210089.210111). The asymptotic efficiency index, $q^{1/k}$, is $(2 + 7^{1/2})^{1/3} = 1.6686...$.

Originally by John Travers.

!!! note
    The paper refenced above shows that for a continuously differentiable $f$ over $[a,b]$ with a simple root  the algorithm terminates at a zero or asymptotically the steps are of the inverse cubic type (Lemma 5.1). This is proved under an assumption that $f$ is four-times continuously differentiable.

