```julia
fit(formula::FormulaTerm, data::DataFrame, modelClass::LogisticRegression, Link::Cloglog; kwargs...)
```

Fit a Logistic Regression model on the input data using the Cloglog link. Uses the [glm](https://juliastats.org/GLM.jl/stable/api/#GLM.glm) method from the [GLM](https://github.com/JuliaStats/GLM.jl) package under the hood. Returns an object of type `FrequentistRegression{:LogisticRegression}`. Supports the same keyword arguments as glm.
