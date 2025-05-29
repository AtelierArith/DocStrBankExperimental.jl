Overall single compute job to do

  * `id::Int64`: CompTask id
  * `user_id::Int64`: user to which this task belong
  * `nodetime_total::Int64`: total nodetime to finish this task, if -1 then no limit
  * `nodetime_left::Int64`: nodetime left to finish this task
  * `nodetime_left_unplanned::Int64`: nodetime left to finish this task including submitted jobs
  * `nodetime_done::Int64`: nodetime completed so far
  * `submit_time::Int64`: Task submit time, the user can start working on it after that time
  * `start_time::Int64`: Task start time
  * `end_time::Int64`: last job end time
  * `task_split_schema::HPCMod.TaskSplitSchema`: Strategy for task splitting
  * `max_concurrent_jobs::Int64`: max concurrent jobs
  * `nodes_prefered::Int64`: prefered number of nodes
  * `walltime_prefered::Int64`: prefered walltime
  * `current_jobs::Vector{Int64}`: current job, 0 if none
  * `jobs::Vector{Int64}`: list of jobs worked on this task
  * `next_check_time::Int64`: Next check time by user, for example send next batch job
