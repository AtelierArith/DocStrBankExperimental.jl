```
@Job(job_description)
```

Constructs a new job based on a description. 

## Description Format

```juila
MyNewJob = @Job begin
    # Paramters are the input values for the job 
    parameters = (param1::String, param2::Int, param)
    
    # Dependencies list jobs that should be inputs to this job (Optional)
    # They can be created programmatically using parameters, and must return an
    # <:AbstractJob, AbstractArray{<:AbstractJob}, or AbstractDict{Symbol, <:AbstractJob}
    dependencies = [[SomeJob(i) for i in 1:param2]; AnotherJob("input")]
    
    # Target is an output location to cache the result. If the target exists, the job will
    # be skipped and the cached result will be returned (Optional).
    target = FileTarget(joinpath(snf_path, "raw_tables", "$month.csv"))
    
    # The process function will be executed when the job is called.
    # All parameters, `dependencies`, and `target` are defined in this scope.
    process = begin
        dep1_data = dependencies[1]
        x = do_logic(dep1_data, param1)
        write(target, x)
        return x
    end
end
```
