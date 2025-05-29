```
AWSBatchManager(max_workers; kwargs...)
AWSBatchManager(min_workers:max_workers; kwargs...)
AWSBatchManager(min_workers, max_workers; kwargs...)
```

A cluster manager which spawns workers via [Amazon Web Services Batch](https://aws.amazon.com/batch/) service. Typically used within an AWS Batch job to add additional resources. The number of workers spawned may be potentially be lower than the requested `max_workers` due to resource contention. Specifying `min_workers` can allow the launch to succeed with less than the requested `max_workers`.

## Arguments

  * `min_workers::Int`: The minimum number of workers to spawn or an exception is thrown
  * `max_workers::Int`: The number of requested workers to spawn

## Keywords

  * `definition::AbstractString`: Name of the AWS Batch job definition which dictates properties of the job including the Docker image, IAM role, and command to run
  * `name::AbstractString`: Name of the job inside of AWS Batch
  * `queue::AbstractString`: The job queue in which workers are submitted. Can be either the queue name or the Amazon Resource Name (ARN) of the queue. If not set will default to the environmental variable "WORKER*JOB*QUEUE".
  * `memory::Integer`: Memory limit (in MiB) for the job container. The container will be killed if it exceeds this value.
  * `region::AbstractString`: The region in which the API requests are sent and in which new worker are spawned. Defaults to "us-east-1". [Available regions for AWS batch](http://docs.aws.amazon.com/general/latest/gr/rande.html#batch_region) can be found in the AWS documentation.
  * `timeout::Period`: The maximum number of seconds to wait for workers to become available before attempting to proceed without the missing workers.

## Examples

```julia
julia> addprocs(AWSBatchManager(3))  # Needs to be run from within a running AWS batch job
```
