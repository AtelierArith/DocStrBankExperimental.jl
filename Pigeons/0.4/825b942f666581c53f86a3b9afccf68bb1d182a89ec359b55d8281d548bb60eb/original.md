Storage involved in PT algorithms:

  * `inputs`: The user-provided [`Inputs`](@ref) that determine the execution of a PT algorithm.

  * `replicas`: The [`replicas`](@ref) held by this machine.

  * `shared`: Information shared across all machines, updated between rounds.

  * `exec_folder`: Either a path to a folder shared by all processes, which is used to save information to disk (checkpoints, samples etc); or nothing if a completely in-memory algorithm is used.

  * `reduced_recorders`: [`recorders`](@ref) from the last round, or empty [`recorders`](@ref).
