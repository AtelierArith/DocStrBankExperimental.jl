HPCResource - HPC Resource struct to track resource occupiency and jobs

  * `nodes::Int64`: number of nodes
  * `node_used_by_job::Vector{Int64}`: array with job id using that node
  * `node_released_at::Vector{Int64}`: the node will be released at time, -1 if already available
  * `node_released_at_sorted::Vector{Int64}`: same as node*released*at but sorted
  * `queue::Vector{HPCMod.BatchJob}`: Jobs in queue
  * `executing::Dict{Int64, HPCMod.BatchJob}`: Jobs currently running
  * `history::Vector{HPCMod.BatchJob}`: Jobs finished
  * `max_nodes_per_job::Int64`
  * `max_time_per_job::Int64`
  * `scheduler_fifo::Bool`
  * `scheduler_backfill::Bool`
  * `stats::HPCMod.HPCResourceStats`
