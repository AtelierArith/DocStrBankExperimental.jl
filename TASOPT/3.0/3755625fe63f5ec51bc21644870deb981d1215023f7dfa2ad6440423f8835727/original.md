Indices of quantities of par arrays selected to be output by default by [`output_csv()`](@ref). Formatted as a Dict() where keys are par array names and values are arrays of indices. Note that this selection is only along the first dimension of par arrays (i.e., selecting quantities, not missions or flight points).

Custom Dicts() can be passed to [`output_csv()`](@ref) following the format: `Dict(){String => Union{AbstractVector,Colon(), Integer}}`. 

For example: 1 : `default_output_indices["parg"] = [1, 5, igtotal]`         > when submitted to `output_csv()`, will output as columns the first, fifth, and last entry of `parg`

2 : `default_output_indices["para"] = Colon() #NOT [Colon()]`         > when submitted to `output_csv()`, will output all indices of `para` (whether all flights or missions are included is controlled by a separate parameter)
