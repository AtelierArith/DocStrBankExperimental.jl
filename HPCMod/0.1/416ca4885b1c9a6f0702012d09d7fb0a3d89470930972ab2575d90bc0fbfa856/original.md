User

  * `id::Int64`
  * `pos::Tuple{Int64}`
  * `max_concurrent_tasks::Int64`: max concurrent tasks
  * `max_nodes_per_job::Int64`: max number of nodes per job, -1 - there is no constrain
  * `max_time_per_job::Int64`: max job walltime per job, -1 - there is no constrain
  * `tasks_to_do::DataStructures.SortedSet{HPCMod.CompTask}`
  * `tasks_active::Vector{HPCMod.CompTask}`
  * `tasks_done::Vector{HPCMod.CompTask}`
  * `jobs_to_process::Vector{HPCMod.BatchJob}`: finished jobs for User to process
  * `inividual_jobs_task::HPCMod.CompTask`: CompTask for inidividual jobs
  * `inividual_jobs::DataStructures.SortedSet{HPCMod.BatchJob}`: jobs which are not bind to task
  * `thinktime_generator::Function`
