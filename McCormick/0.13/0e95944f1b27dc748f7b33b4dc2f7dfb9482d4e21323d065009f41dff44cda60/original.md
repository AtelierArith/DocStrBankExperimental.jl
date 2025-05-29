MC{N,T}(val::Float64, Intv::Interval{Float64}, i::Int64)

Constructs a McCormick relaxation with the convex relaxation equal to `val`, concave relaxation equal to `val`, interval bounds of `Intv`, and a unit subgradient with a nonzero ith dimension of length N.
