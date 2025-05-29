```
skating_combined(dances, results_single_dances)
```

Calculates the final placement of competitors in a dancing competition based on the skating rules. `dances` is a vector of strings, containing the names of the dances.  `results_single_dances` is a vector of DataFrames, containing the results for the individual dances. See [`skating_single_dance`](@ref) for the correct input format.

Outputs a DataFrame with the accumulated skating tableau as strings, a vector containing  tableaus containing the application of Rule 10 and Rule 11, the skating results for the individual dances as well as a DataFrame with the starter numbers and final places.
