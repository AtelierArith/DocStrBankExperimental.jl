```
    z = ePortfolio(mu, aEF::sEF)
    z = ePortfolio(mu, P::Problem; nS=Settings(P), settings, settingsLP)            #one-step, given mu
    z = ePortfolio(P::Problem, L, aCL::Vector{sCL})
    z = ePortfolio(P::Problem, L::T=0.0; nS=Settings(P), settings, settingsLP)      #one-step, given L
```

`ePortfolio(mu::Float64, aEF)` compute the efficient portfolio given mu when Efficient Frontier is known, returns portfolio weights z (Nx1 vector of NaN if mu is out of range)

`ePortfolio(mu, P; nS=Settings(P))` compute the efficient portfolio for `P` given mu::Float64, returns portfolio weights z (Nx1 vector of NaN if mu is out of range) If mu is a ::Vector{Float64}, z is a matrix, its row k is the portfolio weights for mu[k]. Here you can not set `init::Function`

`ePortfolio(P, L::T, aCL)` compute the efficient portfolio for `P` with known Critical Lines `aCL`, given `L::T` (Float64, BigFloat)

`ePortfolio(P::Problem, L::T=0.0; nS=Settings(P), settings, settingsLP)` compute the efficient portfolio for `P` given `L`

See also [`EfficientFrontier.ECL`](@ref), [`eFrontier`](@ref), [`Problem`](@ref), [`Settings`](@ref)
