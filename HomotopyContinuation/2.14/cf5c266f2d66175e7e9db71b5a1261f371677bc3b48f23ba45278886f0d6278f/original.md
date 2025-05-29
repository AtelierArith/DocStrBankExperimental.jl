```
RandomizedSystem(F::Union{System,AbstractSystem}, k::Integer;
        identity_block = true,
        compile = mixed)
```

Given a $n × N$ system `F``this constructs the system``\mathfrak{R}(F; k)(x) = A⋅F(x)``where``A``is a``k × N``matrix. If`identity_block = true`then the first`k`columns of``A`` form an identity matrix. The other entries are random complex numbers. See Chapter 13.5 in [^SW05] for more details.

```
RandomizedSystem(F::Union{System,AbstractSystem}, A::Matrix{ComplexF64};
    identity_block = true,
    compile = mixed)
```

Explicitly provide the used randomization matrix. If `identity = true` then `A` has to be `k × (n - k)` matrix. Otherwise `A` has to be a `k × n` matrix..

[^SW05]: Sommese, A. J., & Wampler, C. W. (2005). The Numerical Solution of Systems of Polynomials Arising in Engineering and Science. World Scientific.
