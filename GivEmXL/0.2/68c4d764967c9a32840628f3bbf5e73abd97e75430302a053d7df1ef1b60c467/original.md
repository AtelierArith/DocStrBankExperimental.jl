```
proc_data(xlfile, datafiles, paramsets, procwhole_fn, procsubset_fn, postproc_fn; throwonerr=false) 
    → (; overview, subsets_results, résumé, errors)
```

Calls the user provided data processing functions.

# Arguments

  * `xlfile`: XLSX file (if any)
  * `datafiles`: Data file(s) or folder (if any)
  * `paramsets::Vector{NamedTuple}`: Parameter merged from those supplied by user as cli arguments and those contained in the excel file.
  * `procwhole_fn::Union{Nothing, Function}`: User supplied function for preprocessing
  * `procsubset_fn::Union{Nothing, Function}`: User supplied function for processing a data subset
  * `postproc_fn::Union{Nothing, Function}`: User supplied function for postprocessing

# Keyword arguments

  * `throwonerr=false`: If `true`, `Julia` execution will stop on an error and print error information, otherwise execution continues    and error information can be saved into a separate file.

# Returned NamedTuple

  * `overview::NamedTuple`: May contain `DataFrame`(s) and plot objects as returned by `procwhole_fn` function
  * `subsets_results::Vector{NamedTuple}`: May contain a `DataFrame` row and plot objects for each subset as returned by `procsubset_fn`
  * `résumé::NamedTuple`: May contain `DataFrame`(s) and plot objects as returned by `postproc_fn` function
  * `errors::Vector{NamedTuple}`: Collects information on errors if any occurred.

Function `proc_data` is public, not exported.
