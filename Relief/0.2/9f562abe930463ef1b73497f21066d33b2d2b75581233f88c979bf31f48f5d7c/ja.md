function ecrelieff(data::Array{<:Real,2}, target::Array{<:Integer,1}, m, k,                      dist*func::Any=(e1, e2) -> sum(abs.(e1 .- e2), dims=2);                      mode::String="k*nearest", sig::Real=1.0, f_type::String="continuous")::Array{Int64,1}

特徴ランキングを蒸発冷却ReliefFアルゴリズムを使用して計算します。

---

# 参考文献:

  * B.A. McKinney, D.M. Reif, B.C. White, J.E. Crowe, Jr., J.H. Moore.

相互作用を含む遺伝子型データのための蒸発冷却特徴選択。
