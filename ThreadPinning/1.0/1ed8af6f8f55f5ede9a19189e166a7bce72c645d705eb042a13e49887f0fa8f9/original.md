Returns a `Dict{Int, String}` where the keys are the pids of the Julia workers and the values are the hostnames of the nodes that are currently hosting the respective workers.

If `include_master=true`, the master process (`Distributed.myid() == 1`) will be included.
