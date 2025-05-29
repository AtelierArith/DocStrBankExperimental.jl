Output writer for a JLD2 file that saves the PrognosticVariables and DiagnosticVariables structs directly to a JLD2 file. All internal scalings and units are still applied to these outputs. Fields are 

  * `active::Bool`
  * `path::String`: [OPTION] path to output folder, run_???? will be created within
  * `id::String`: [OPTION] run identification number/string
  * `run_path::String`
  * `filename::String`: [OPTION] name of the output jld2 file
  * `write_restart::Bool`: [OPTION] also write restart file if output==true?
  * `pkg_version::VersionNumber`
  * `output_dt::Dates.Second`: [OPTION] output frequency, time step
  * `merge_output::Bool`: [OPTION] will reopen and resave the file to merge everything in one big vector. Turn off if the file is too large for memory.
  * `output_prognostic::Bool`: [OPTION] output the PrognosticVariables
  * `output_diagnostic::Bool`: [OPTION] output the DiagnosticVariables as well
  * `output_every_n_steps::Int64`
  * `timestep_counter::Int64`
  * `output_counter::Int64`
  * `jld2_file::Union{Nothing, JLD2.JLDFile}`
