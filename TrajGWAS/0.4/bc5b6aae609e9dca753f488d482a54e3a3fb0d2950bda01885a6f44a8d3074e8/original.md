Returns covrowmask, geneticrowmask for matching indicies in a covariate file and geneticfile. Input the mean, random effects, and within-subject variance formulas, the grouping (id) variable, the dataframe (or table), and a vector of the IDs in the order of the genetic file. 

```julia
covrowinds, geneticrowinds = matchindices(@formula(y ~ 1 + x), 
    @formula(y ~ 1), 
    @formula(y ~ 1 + z), 
    idvar, df, geneticsamples)

```
