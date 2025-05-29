```
update!(lk::Link, x; s::Symbol=:sta)
update!(lk::Link, arg::Args)
update!(name::Symbol, ....)
```

Update an actor's internal state `s` with `args...`.

# Arguments

  * actor `lk::Link` or `name::Symbol` if registered,
  * `x`: value/variable to update the choosen state with,
  * `arg::Args`: arguments to update,
  * `s::Symbol`: one of `:arg`, `:mode`, `:name`, `:self`, `:sta`, `:usr`.

*Note:* If you want to update the stored arguments to the  behavior function with `s=:arg`, you must pass an [`Args`](@ref)  to `arg`. If `Args` has keyword arguments, they are merged  with existing keyword arguments to the behavior function.

# Example

```julia
julia> update!(fact, 5)       # update the state variable
Actors.Update(:sta, 5)

julia> query(fact, :sta)      # query it
5

julia> update!(fact, Args(0, u=5, v=5));  # update arguments to the behavior 

julia> call(fact, 0)          # call the actor with 0
10
```
