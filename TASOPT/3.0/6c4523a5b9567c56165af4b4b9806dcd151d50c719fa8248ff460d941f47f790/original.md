```
output_csv(ac::TASOPT.aircraft=TASOPT.load_default_model(), 
        filepath::String=joinpath(TASOPT.__TASOPTroot__, "IO/default_output.csv");
        overwrite::Bool = false, indices::Dict = default_output_indices,
        includeMissions::Union{AbstractVector,Colon,Bool,Integer} = false, 
        includeFlightPoints::Union{AbstractVector,Colon,Bool,Integer} = false,
        forceMatrices::Bool = false)
```

writes the values of `ac` to CSV file `filepath` with index variables as headers.  A typical set of values is output by default for the design mission at the first cruise point. Appends to extant `filepath` if headers are compatible, appending integer suffixes to filename when not.

Output is customizable by:

  * `indices`: specifies the desired indices of each par array,
  * `includeMissions`: allows output of all missions (i.e., =true) or specifiable indices (e.g., =[1,2,3]),
  * `includeFlightPoints`: allows output of all flight points (as for `includeMissions`).

!!! details "🔃 Inputs and Outputs"
    **Inputs:**

      * `ac::TASOPT.aircraft`: TASOPT aircraft `struct` containing model in any state.
      * `filepath::String`: path and name of .csv file to be written.
      * `overwrite::Bool`: deletes existing file at filepath when true, default is false.
      * `indices::Dict{String => Union{AbstractVector,Colon(), Integer}}`: specifies desired indices of par arrays given as keys. Customizable; built-in options: [`default_output_indices`](@ref), `output_indices_all`, and `output_indices_wEngine`.
      * `includeMissions::Union{AbstractVector,Colon,Bool,Integer}`: saves all mission entries as an array in a CSV cell when true, default is false, inner nested array when flight points are also output. specific indices can also be specified as Vectors of Ints.
      * `includeFlightPoints::Union{AbstractVector,Colon,Bool,Integer}`: saves all flight point entries as an array in a CSV cell when true, default is false, outer nested array when missions are also output. specific indices can also be specified as Vectors of Ints.
      * `forceMatrices::Bool`: forces all entries that vary with mission and flight point to follow nested array structure
      * `struct_excludes::AbstractVector{String}`: names/substrings of fields to exclude from output of ac struct. Default is `[]`, excluding nothing.

    **Outputs:**

      * `newfilepath::String`: actual output filepath; updates in case of header conflicts. same as input filepath if `overwrite = true`.

