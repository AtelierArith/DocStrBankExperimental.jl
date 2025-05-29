TaskData type, which is the supertype for all data structs,  which shall describe a specific task type. Together with a new method execute task for the inherting struct, new types of tasks can be introduced.

# Example

```julia
struct InstantTaskData <: TaskData end
function execute_task(f::Function, scheduler::AbstractScheduler, data::InstantTaskData)
    f()
end
```
