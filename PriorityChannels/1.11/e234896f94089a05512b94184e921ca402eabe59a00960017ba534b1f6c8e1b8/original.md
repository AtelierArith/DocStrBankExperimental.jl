```
PriorityChannel(func::Function; ctype=Any, csize=1, taskref=nothing)
```

Create a new task from `func`, bind it to a new channel of type `ctype` and size `csize`, and schedule the task, all in a single call.

`func` must accept the bound channel as its only argument.

If you need a reference to the created task, pass a `Ref{Task}` object via keyword argument `taskref`.

Return a `PriorityChannel`.

# Examples

```jldoctest
julia> chnl = PriorityChannel(c->foreach(i->put!(c,i), 1:4));

julia> typeof(chnl)
PriorityChannel{Any,Int64}

julia> for i in chnl
           @show i
       end;
i = 1
i = 2
i = 3
i = 4
```

Referencing the created task:

```jldoctest
julia> taskref = Ref{Task}();

julia> chnl = PriorityChannel(c->(@show take!(c)); taskref=taskref);

julia> istaskdone(taskref[])
false

julia> put!(chnl, "Hello");
take!(c) = "Hello"

julia> istaskdone(taskref[])
true
```
