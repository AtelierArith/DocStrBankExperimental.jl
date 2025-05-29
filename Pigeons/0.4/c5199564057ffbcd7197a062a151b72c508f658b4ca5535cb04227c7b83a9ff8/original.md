Flag to run on MPI. Before using, you have to call once [`setup_mpi`](@ref).

Fields: 

  * `n_threads`: The number of threads per MPI process, 1 by default.

  * `walltime`: The walltime limit, 00:30:00 by default (i.e., 30 minutes).

  * `n_mpi_processes`: The number of MPI processes, 2 by default.

  * `memory`: The memory allocated to each MPI process, 8gb by default.

  * `dependencies`: Julia modules (if of type `Module`) or paths to include (if of type `String`) needed by the child process.

  * `mpiexec_args`: Extra arguments passed to mpiexec.
