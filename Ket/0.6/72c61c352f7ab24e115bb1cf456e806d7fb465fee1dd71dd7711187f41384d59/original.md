```
schmidt_number(
    ρ::AbstractMatrix{T},
    s::Integer = 2,
    dims::AbstractVecOrTuple = _equal_sizes(ρ),
    n::Integer = 1;
    ppt::Bool = true,
    verbose::Bool = false,
    solver = Hypatia.Optimizer{_solver_type(T)})
```

Upper bound on the white noise robustness of `ρ` such that it has a Schmidt number `s`.

If a state $ρ$ with local dimensions $d_A$ and $d_B$ has Schmidt number $s$, then there is a PSD matrix $ω$ in the extended space $AA'B'B$, where $A'$ and $B'$ have dimension $s$, such that $ω / s$ is separable  against $AA'|B'B$ and $Π^† ω Π = ρ$, where $Π = 1_A ⊗ s ψ^+ ⊗ 1_B$, and $ψ^+$ is a non-normalized maximally entangled state. Separabiity is tested with the DPS hierarchy, with `n` controlling the how many copies of the $B'B$ subsystem are used.

References:

  * Hulpke, Bruss, Lewenstein, Sanpera, [arXiv:quant-ph/0401118](https://arxiv.org/abs/quant-ph/0401118)
  * Weilenmann, Dive, Trillo, Aguilar, Navascués, [arXiv:1912.10056](https://arxiv.org/abs/1912.10056)
