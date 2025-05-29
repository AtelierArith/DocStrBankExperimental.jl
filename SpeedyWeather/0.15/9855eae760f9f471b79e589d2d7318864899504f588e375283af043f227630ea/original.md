Clock struct keeps track of the model time, how many days to integrate for and how many time steps this takes.

  * `time::Dates.DateTime`: current model time
  * `start::Dates.DateTime`: start time of simulation
  * `period::Dates.Second`: period to integrate for
  * `timestep_counter::Int64`: Counting all time steps during simulation
  * `n_timesteps::Int64`: number of time steps to integrate for, set in `initialize!(::Clock, ::AbstractTimeStepper)`
  * `Δt::Dates.Millisecond`: Time step
