```
SamplerUniformMeetAny(constraint::MeetAny, H::Int64)
```

Pre-compute data for uniformly sampling `BitVector` objects from a [`MeetAny`](@ref) constraint. The sampled vectors will have length `H`.

The algorithm used is the recursive RGA due to Bernardi, Olivier, and Omer Giménez, "A  linear algorithm for the random sampling from regular languages." Algorithmica 62.1  (2012): 130-145.

# Examples

```julia-repl
julia> sp = SamplerUniformMeetAny(MeetAny(1, 3), 10);

julia> rand(sp)
10-element BitVector:
1
1
0
1
1
0
1
0
0
1
```
