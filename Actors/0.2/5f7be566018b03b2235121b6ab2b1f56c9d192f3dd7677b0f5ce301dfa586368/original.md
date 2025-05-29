```
query(lk::Link, [from::Link,] s::Symbol; timeout::Real=5.0)
query(name::Symbol, ....)
```

Query an actor about an internal state variable `s`. 

# Parameters

  * actor `lk::Link` or `name::Symbol` if registered,
  * `from::Link`: sender link,
  * `s::Symbol` one of `:mode`,`:bhv`,`:res`,`:sta`,`:usr`.
  * `timeout::Real=5.0`:

**Note:** If `from` is omitted, `query` blocks and returns  the response. In that case there is a `timeout`.

# Examples

```julia
julia> f(x, y; u=0, v=0) = x+y+u+v  # implement a behavior
f (generic function with 1 method)

julia> fact = spawn(Bhv(f, 1))     # start an actor with it
Link{Channel{Any}}(Channel{Any}(sz_max:32,sz_curr:0), 1, :default)

julia> query(fact, :mode)           # query the mode
:default

julia> cast(fact, 1)                # cast a 2nd argument to it
Actors.Cast((1,))

julia> query(fact, :res)            # query the result
2

julia> query(fact, :sta)            # query the state

julia> query(fact, :bhv)            # query the behavior
Bhv(f, (1,), Base.Iterators.Pairs{Union{},Union{},Tuple{},NamedTuple{(),Tuple{}}}(), Actors.var"#2#4"{Base.Iterators.Pairs{Union{},Union{},Tuple{},NamedTuple{(),Tuple{}}},typeof(f),Tuple{Int64}}(Base.Iterators.Pairs{Union{},Union{},Tuple{},NamedTuple{(),Tuple{}}}(), f, (1,)))
```
