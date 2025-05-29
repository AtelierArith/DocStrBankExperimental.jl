`profit!(pl::PLInvestments, r_distr::Vector{Float64}, s::Real)`

Updates `pl.profit`, where `r_distr` is the investment result  and `s` is the risk free interest rate. Only the investment  return above `s` counts as profit.
