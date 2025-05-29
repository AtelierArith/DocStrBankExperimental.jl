print: output formatting. return a DataFrame.

`print(:: ListofStates; verbose :: Bool = true, print_sym :: Union{Nothing,Array{Symbol,1}})`

Note:

  * set `verbose` to false to avoid printing.
  * if `print_sym` is an Array of Symbol, only those symbols are printed. Note that

the returned DataFrame still contains all the columns.

  * More information about DataFrame: http://juliadata.github.io/DataFrames.jl

see also: add_to_list!, length, ListofStates
