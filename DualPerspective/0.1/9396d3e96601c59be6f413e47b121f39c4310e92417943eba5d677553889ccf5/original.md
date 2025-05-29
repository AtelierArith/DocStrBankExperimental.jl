Solve the LP problem:

```
min ⟨c, x⟩
subject to Ax = b, x ≥ 0
```

using the self-scaled solver by solving the regularized problem:

```
minimize_{x ∈ ℝ₊ⁿ} (1/(2λ)) * ||Ax - b||² + ⟨c, x⟩ + ε * H(x)
```

which is equivalent to:

```
minimize_{x ∈ ℝ₊ⁿ} (1/(2λε)) * ||Ax - b||² + ⟨c/ε, x⟩ + H(x)
```

where ε is the relaxation constant, λ is the feasibility constant, and H(x) is the entropy function.
