Simulation parameters.

  * `iters::Int64`: Number of iterations for US
  * `steps::Int64`: MC steps for a run or single iteration
  * `max_bias_diff::Float64`: Maximum change in bias energy (kbT)
  * `write_interval::Int64`: Number of steps between writing to output files
  * `radius_move_freq::Float64`: Frequency of radius moves (the remainder are filament translation moves)
  * `filebase::String`: Output filebase (include filepath)
  * `analytical_biases::Bool`: Use analytical model to generation starting biases
  * `read_biases::Bool`: Read starting biases from file
  * `biases_filename::String`: File to read biases from
  * `restart_iter::Int64`: Iteration to to start on
  * `binwidth::Int64`: Width of bins for lattice height bias (set to 1 for no binning)
