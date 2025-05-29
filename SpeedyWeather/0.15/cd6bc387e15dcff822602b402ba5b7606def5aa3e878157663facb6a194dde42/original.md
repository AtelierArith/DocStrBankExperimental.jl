Feedback struct that contains options and object for command-line feedback like the progress meter.

  * `verbose::Bool`: print feedback to REPL?, default is isinteractive(), true in interactive REPL mode
  * `debug::Bool`: check for NaRs in the prognostic variables
  * `output::Bool`: write a progress.txt file? State synced with NetCDFOutput.output
  * `id::String`: identification of run, taken from ::OutputWriter
  * `run_path::String`: path to run folder, taken from ::OutputWriter
  * `progress_meter::ProgressMeter.Progress`: struct containing everything progress related
  * `progress_txt::IOStream`: txt is a Nothing in case of no output
  * `nars_detected::Bool`: did Infs/NaNs occur in the simulation?
