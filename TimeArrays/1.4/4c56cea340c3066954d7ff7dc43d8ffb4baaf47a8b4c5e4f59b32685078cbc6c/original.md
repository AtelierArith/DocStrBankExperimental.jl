```
TimeArray(iter)
TimeArray{T,V}(iter)
```

Creates a `TimeArray{T,V}` object from `iter` values and sorts them by date in ascending order.

```jldoctest
julia> struct TimeTickIter
           state::Int
       end;

julia> Base.length(x::TimeTickIter) = x.state;

julia> function Base.iterate(x::TimeTickIter, state = 1)
           return state <= x.state ? (TimeTick(state, state), state + 1) : nothing
       end;

julia> TimeArray(TimeTickIter(5))
5-element TimeArray{Int64, Int64}:
 TimeTick(1, 1)
 TimeTick(2, 2)
 TimeTick(3, 3)
 TimeTick(4, 4)
 TimeTick(5, 5)

julia> TimeArray{Float64,Float64}(TimeTickIter(5))
5-element TimeArray{Float64, Float64}:
 TimeTick(1.0, 1.0)
 TimeTick(2.0, 2.0)
 TimeTick(3.0, 3.0)
 TimeTick(4.0, 4.0)
 TimeTick(5.0, 5.0)
```
