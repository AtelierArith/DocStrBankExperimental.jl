Flag to run to a new julia  process. Useful e.g. to dynamically control  the number of threads to use or to use MPI on a  single machine. 

Fields: 

  * `n_threads`: The number of threads to provide in the child julia process, the same as the current process by default.

  * `dependencies`: Julia modules (if of type `Module`) or paths to include (if of type `String`) needed by the child process.

  * `n_local_mpi_processes`: If greater than one, run the code locally over MPI using that many MPI processes. In most cases, this is useful only for debugging purpose, as multi-threading should typically perform better. This could also potentially be useful if using a third-party target distribution which somehow does not support multi-threading.

  * `wait`: If wait is false, the process runs asynchronously. When wait is false, the process' I/O streams are directed to devnull.

  * `mpiexec_args`: Extra arguments passed to mpiexec.
