```
@submit [option=value]... expr
```

Submit a job from `expr`. If a `Job` is **explicitly** shown in `expr`, `DONE => job` will be automatically added to the dependency list. 

  * `expr`: any type of `Expr`ession is supported.
  * `option = value`: kwargs of [`Job`](@ref). If `expr` is parsed to be a `Pipelines.Program`, `option`s also include its inputs, outputs and run kwargs.

See also [`Job`](@ref), [`submit!`](@ref)

## Example

```julia
j = @submit 1+1
wait(j)
@assert result(j) == 2

# you can use any keyword arguments that `Job` supports, such as `name`, `ncpu`:
j_2sec = @submit name = "run after 2 sec" begin sleep(2); 32 end

# because `j_2sec isa Job`, `DONE => j_2sec` is pushed to `j2.dependency`.
j2 = @submit mem=2KB begin
    1 + result(j_2sec)
end

wait(j2)
@assert result(j2) == 1 + 32

# you can also manually add dependencies not in the `expr`:
j3 = @submit dependency = [PAST => j] println("j3 finished. result of j2 = ", result(j2))

# Note: j3.dependency might be empty after submit, because JobScheduler will remove jobs that reached their states in the dependency list.
```

!!! warning "Only explicit jobs can be automatically added to dependency"
    `@submit` cannot know the elements in a container, so it is unable to walk through and add Job dependencies in a container.

    ```julia
    jobs = Job[]  # the job container
    for i in 1:2
        push!(jobs, @submit begin sleep(30);i end) # 10 jobs will be added to `jobs`
    end

    x = 0
    j_something_wrong = @submit for j in jobs
        # have to use global x
        global x += result(j)
    end
    # ┌ Warning: Getting result from a running job: returned value might be unexpected.
    # └ @ JobSchedulers ~/projects/JobSchedulers.jl/src/jobs.jl:318

    result(j_something_wrong)
    # MethodError(+, (nothing, nothing), 0x0000000000007b16)
    ```

    To avoid it, we can       (1) use `submit!`, or      (2) explicitly add `dependency = jobs` to `@submit`.

    ```julia
    x = 0
    j_ok = submit!(dependency = jobs) do
        for j in jobs
            # have to use global x
            global x += result(j)
        end
    end
    wait(j_ok)
    @assert x == 55

    x = 100
    j_ok_too = @submit dependency = jobs for j in jobs
        # have to use global x
        global x += result(j)
    end
    wait(j_ok_too)
    @assert x == 155
    ```

