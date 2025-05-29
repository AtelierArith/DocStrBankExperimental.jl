`profit!(pl::PLInvestments, r_distr::Vector{Float64}, s::Real)`

`pl.profit`を更新します。ここで、`r_distr`は投資結果であり、`s`はリスクフリー金利です。`s`を上回る投資収益のみが利益としてカウントされます。
