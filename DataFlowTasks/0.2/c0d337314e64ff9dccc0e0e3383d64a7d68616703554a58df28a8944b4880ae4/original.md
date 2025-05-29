```
@dspawn expr [kwargs...]
```

Spawn a Julia `Task` to execute the code given by `expr`, and schedule it to run on any available thread.

Annotate the code in `expr` with `@R`, `@W` and/or `@RW` to indicate how it accesses data (see examples below). This information is used to automatically infer task dependencies.

Additionally, the following keyword arguments can be provided:

  * `label`: provide a label to identify the task. This is useful when logging scheduling information;
  * `priority`: inform the scheduler about the relative priority of the task. This information is not (yet) leveraged by the default scheduler.

## Examples:

Below are 3 equivalent ways to create the same `Task`, which expresses a Read-Write dependency on `C` and Read dependencies on `A` and `B`

```jldoctest; output = false
using LinearAlgebra
using DataFlowTasks
A = ones(5, 5)
B = ones(5, 5)
C = zeros(5, 5)
α, β = (1, 0)

# Option 1: annotate arguments in a function call
@dspawn mul!(@RW(C), @R(A), @R(B), α, β)

# Option 2: specify data access modes in the code block
@dspawn begin
   @RW C
   @R  A B
   mul!(C, A, B, α, β)
end

# Option 3: specify data access modes after the code block
# (i.e. alongside keyword arguments)
res = @dspawn mul!(C, A, B, α, β) @RW(C) @R(A,B)

fetch(res) # a 5×5 matrix of 5.0

# output

5×5 Matrix{Float64}:
 5.0  5.0  5.0  5.0  5.0
 5.0  5.0  5.0  5.0  5.0
 5.0  5.0  5.0  5.0  5.0
 5.0  5.0  5.0  5.0  5.0
 5.0  5.0  5.0  5.0  5.0
```

Here is a more complete example, demonstrating a full computation involving 2 different tasks.

```jldoctest
using DataFlowTasks

A = rand(5)

# create a task with WRITE access mode to A
# and label "writer"
t1 = @dspawn begin
    @W A
    sleep(1)
    fill!(A,0)
    println("finished writing")
end  label="writer"

# create a task with READ access mode to A
t2 = @dspawn begin
    @R A
    println("I automatically wait for `t1` to finish")
    sum(A)
end  priority=1

fetch(t2) # 0

# output

finished writing
I automatically wait for `t1` to finish
0.0
```

Note that in the example above `t2` waited for `t1` because it read a data field that `t1` accessed in a writable manner.
