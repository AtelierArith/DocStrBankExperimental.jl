```
contr(df::DataFrames.DataFrame, cVars::AbstractArray{Symbol,1}, 
      cTypes::AbstractArray{String,1}=repeat(["treat"], inner=length(cVars)), 
      trtRefs::AbstractArray= repeat([nothing], inner=length(cVars)))
```

Converts categorical variables in a DataFrame to specified contrast types.  All other variables are left as-is. 

# Arguments

  * `df::DataFrames.DataFrame`: DataFrame of variables
  * `cVar::Symbol`: symbol for the categorical variable in df to be converted
  * `cTypes::AbstractArray{String,1}`: 1d array of character strings of the same length as `cVars`,  indicating the types of contrasts to use. Defaults to treatment contrasts  ("treat") for all variables in `cVars`. Other options include "sum" for sum  contrasts, "noint" for treatment contrasts with no intercept, and  "sumnoint" for sum contrasts with no intercept. For "treat" `cTypes`, you  can also specify the level to use as the reference treatment using `trtRefs`.
  * `trtRefs::AbstractArray`: optional 1d array of character strings of the same length as  `cVars`, specifying the level to use as the references for treatment  contrasts. Defaults to nothing for all variables in `cVars`.

# Value

DataFrame with same variables as the original DataFrame, but categorical  variables converted to dummy contrasts. 

# Some notes

If `cVars` consists of only an empty Symbol, i.e. `cVars=[Symbol()]`, this  will signal to the function that no contrasts should be created. The  original DataFrame will be returned. 
