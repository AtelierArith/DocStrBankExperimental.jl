```
onthread(f::F, tid::Int; wait::Bool=true) where {F<:Function}
```

Execute a function `f` on thread `tid`. 

To execute `f` on a thread other than 1 can speed it up  significantly if it depends on asynchronous tasks.

# Arguments

  * `f::Function`:     function to execute
  * `tid::Int`:        thread id
  * `wait::Bool=true`: if true, it waits for function to finish

# Example

```jldoctest
julia> using DiscreteEvents, .Threads

julia> onthread(2) do; threadid(); end
2
```
