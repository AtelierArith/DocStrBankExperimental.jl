Returns a `Dict{Int, Vector{Int}}` where the keys are the pids of the Julia workers and the values are the CPU IDs of the CPU-threads that are currently running the Julia threads of the worker.

If `include_master=true`, the master process (`Distributed.myid() == 1`) will be included.
