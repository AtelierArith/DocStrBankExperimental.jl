```
soslyap(s::AbstractSwitchedSystem, d; optimizer_constructor=nothing)
```

Find Sum-of-Squares Lyapunov functions; i.e. solves [(5), PJ08] or gives moment matrices certifying the infeasibility of the problem. Use [`ScaledHybridSystem`](@ref) to use a different growth rate than 1.

[PJ08] P. Parrilo and A. Jadbabaie. *Approximation of the joint spectral radius using sum of squares*. Linear Algebra and its Applications, Elsevier, **2008**, 428, 2385-2402
