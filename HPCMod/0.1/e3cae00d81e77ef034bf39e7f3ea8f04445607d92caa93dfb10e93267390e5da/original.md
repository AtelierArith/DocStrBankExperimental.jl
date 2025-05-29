a batch job represent a manageble portion of CompTask

  * `id::Int64`: Job id - smaller id does not nessesary guaranee ealier submition
  * `task::HPCMod.CompTask`
  * `nodes::Int64`
  * `walltime::Int64`
  * `submit_time::Int64`
  * `start_time::Int64`
  * `end_time::Int64`
  * `scheduled_by::HPCMod.SchedulerType`
  * `nodes_list::Vector{Int64}`: Vector with node ids
