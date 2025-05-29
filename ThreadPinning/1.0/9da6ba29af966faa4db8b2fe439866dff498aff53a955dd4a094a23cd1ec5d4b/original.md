Returns a `Dict{Int, Vector{Bool}}` where the keys are the pids of the Julia workers and the values are the results of `ThreadPinning.ispinned` evaluated for all Julia threads of a worker.

If `include_master=true`, the master process (`Distributed.myid() == 1`) will be included.
