```
compute(::AbstractLimbDark, orbit::AbstractOrbit, t, r)
```

Compute the relative flux by calculating the impact parameter at time `t` from the given orbit. The time needs to be compatible with the period of the orbit, nominally in days.

# Examples

```jldoctest orb
julia> using Orbits

julia> ld = PolynomialLimbDark([0.4, 0.26]);

julia> orbit = SimpleOrbit(period=3, duration=1);

julia> ld(orbit, 0, 0.1) # primary egress
0.9878664434953113

julia> ld(orbit, 0.1, 0.1) # 0.1 d
0.9879670695533511
```

this works effortlessly with libraries like [Unitful.jl](https://github.com/painterqubits/Unitful.jl)

```jldoctest orb
julia> using Unitful

julia> orbit = SimpleOrbit(period=3u"d", duration=3u"hr");

julia> ld(orbit, 0u"d", 0.1)
0.9878664434953113
```
