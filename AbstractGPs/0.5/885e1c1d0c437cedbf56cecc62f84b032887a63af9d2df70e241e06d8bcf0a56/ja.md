```
approx_log_evidence(dtc::DTC, fx::FiniteGP, y::AbstractVector{<:Real})
```

決定論的トレーニング条件 (DTC) [1]。`y` は `fx` の観測値であり、`v.z` は誘導点です。

```jldoctest
julia> f = GP(Matern52Kernel());

julia> x = randn(1000);

julia> z = range(-5.0, 5.0; length=256);

julia> d = DTC(f(z));

julia> y = rand(f(x, 0.1));

julia> isapprox(approx_log_evidence(d, f(x, 0.1), y), logpdf(f(x, 0.1), y); atol=1e-6, rtol=1e-6)
true
```

[1] - M. Seeger, C. K. I. Williams and N. D. Lawrence. "Fast Forward Selection to Speed Up Sparse Gaussian Process Regression". In: Proceedings of the Ninth International Workshop on Artificial Intelligence and Statistics. 2003
