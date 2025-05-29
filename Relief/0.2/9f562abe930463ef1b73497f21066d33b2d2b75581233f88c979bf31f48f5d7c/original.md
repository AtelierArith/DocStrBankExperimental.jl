function ecrelieff(data::Array{<:Real,2}, target::Array{<:Integer,1}, m, k,                      dist*func::Any=(e1, e2) -> sum(abs.(e1 .- e2), dims=2);                      mode::String="k*nearest", sig::Real=1.0, f_type::String="continuous")::Array{Int64,1}

Compute feature rankings using Evaporative Cooling ReliefF algorithm.

---

# Reference:

  * B.A. McKinney, D.M. Reif, B.C. White, J.E. Crowe, Jr., J.H. Moore.

Evaporative cooling feature selection for genotypic data involving interactions.
