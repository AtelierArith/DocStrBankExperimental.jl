```
params = fit_adsorption_isotherm(df, pressure_col_name, loading_col_name, model)
```

Takes in a DataFrame `df` containing adsorption isotherm data and fits an analytical model to the data to identify its parameters of best fit, returned as a dictionary. Available models are `:henry` and `:langmuir`

The Henry model takes the following form: N = HP The identified Henry coefficient is `params["H"]`.

The Langmuir model takes the following form: N = (MKP)/(1+KP) where N is the total adsorption, M is the maximum monolayer coverage, K is the Langmuir constant. and P is the pressure of the gas.

# Arguments

  * `df::DataFrame`: The DataFrame containing the pressure and adsorption data for the isotherm
  * `pressure_col_name::Symbol`: The header of the pressure column. Can be found with `names(df)`
  * `loading_col_name::Symbol`: The header of the loading/adsorption column. Can be found with `names(df)`
  * `model::Symbol`: The model chosen to fit to the adsorption isotherm data

# Returns

  * `params::Dict{AbstractString, Float64}`: A Dictionary with the parameters corresponding to each model along with the MSE of the fit. `:langmuir` contains "M" and "K". `:henry` contains "H".
