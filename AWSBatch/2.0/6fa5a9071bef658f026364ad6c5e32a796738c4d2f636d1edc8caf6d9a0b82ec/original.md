```
create_job_queue(name, envs, priority=1; aws_config=global_aws_config())
```

Create a job queue with name `name` and priority `priority` returning the associated `JobQueue` object. `envs` must be an iterator of compute environments given by ARN.

See the AWS docs [here](https://docs.aws.amazon.com/batch/latest/APIReference/API_CreateJobQueue.html).
