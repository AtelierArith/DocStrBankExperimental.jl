```
complete_interact(pp0, pps, proc_data_fn::Function; kwargs...) → nothing
complete_interact(pp0, pps, proc_data_fns::Tuple; kwargs...) → nothing
```

This is the top level function for building the interaction with the user. See the flow diagram in the documentation for details. It calls [`proc_ARGS`](@ref) first, [`prompt_and_parse`](@ref) multiple times, and lets user pick file(s) by a GUI.  The inputs are merged with the parameter in the excel file, and all that passed to user-provided function(s) to perform the data processing.

# Arguments

  * `pp0::Union{Nothing, ArgumentParser}`: ArgumentParser for command line arguments.
  * `pps::NamedTuple`: ArgumentParsers for individual dialogs. The corresponding keys are:    `[:gen_options, :spec_options, :exelfile_prompt, :datafiles_prompt, :next_file]`. To skip a dialog, skip the key.
  * `proc_data_fn(; xlfile, datafiles, paramsets)::Function`: Function to do the actual data processing. It takes these three kwargs.
  * `proc_data_fns::Tuple`: Alternatively a tuple of three functions can be provides:    For preprocessing, processing a subset, and postprocessing. See also [`proc_data`](@ref)

# Keyword arguments

  * `basedir=nothing`: The base directory for the file selection dialogs. If `basedir` not provided, uses the cached value.
  * `paramtables = (;setup="params_setup", exper="params_experiment")`: The names of the tables containing the corresponding parameters.   Set a table to `nothing` to skip it.
  * `getexel=false`: If true, execute excel file selection dialog.
  * `getdata=(; dialogtype = :none)`: If `:none`, no data file selection dialog,    otherwise the parameter will be passed to the [`get_data`](@ref) function to execute file/directory selection dialog.

Function `complete_interact` is exported.
