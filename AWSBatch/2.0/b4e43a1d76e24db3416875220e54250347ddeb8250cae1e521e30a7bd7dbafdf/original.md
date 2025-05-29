```
create_compute_environment(name;
                           managed=true,
                           role="",
                           resources=Dict(),
                           enabled=true,
                           tags=Dict(),
                           aws_config=global_aws_config())
```

Create a compute environment of type `type` with name `name`.

See the AWS docs [here](https://docs.aws.amazon.com/batch/latest/APIReference/API_CreateComputeEnvironment.html).
