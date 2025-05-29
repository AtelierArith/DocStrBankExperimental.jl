```
getnodeheights_majortree(net, checkpreorder::Bool=true; warn=true)
```

Vector of node heights from the major tree, that is: the distance from the root to each node when considering the major tree for node heights. 

missing edge lengths:

  * An error is thrown if a tree edge has a missing edge length.
  * If all parent hybrid edges have missing lengths at a given hybrid node, then the hybrid node is assumed to be as close to the root as possible, that is, the reticulation is assumed "zipped-up" with one of its hybrid edges of length 0.
  * If a major hybrid edge has a missing length, then the hybrid node height will be calculated using the node height and edge length of the minor parent with the largest inheritance γ (with a warning). If the major hybrid edge lacks a length and all non-missing minor edges lack an inheritance γ or have the same value, then an error is thrown.

A warning is issued, unless `warn=false`, if the network is not time-consistent.

See also: [`istimeconsistent`](@ref), [`getnodeheights`](@ref) and [`getnodeheights_average`](@ref).

```jldoctest
#node heights of time-consistent networks are the same 
julia> consistent_net = readnewick("((A:2.5,#H1:1.5::0.4):0.25,(C:1.5,(B:1)#H1:0.5::0.6):1.25);");

julia> heights = getnodeheights(consistent_net)
7-element Vector{Float64}:
 0.0
 1.25
 2.75
 0.25
 1.75
 2.75
 2.75

julia> heights_average = getnodeheights_average(consistent_net);

julia> heights_major = getnodeheights_majortree(consistent_net);

julia> heights == heights_average == heights_major  
true
```

```jldoctest
#inconsistent networks give different results
julia> inconsistent_net = readnewick("((A:2.5,#H1:1.5::0.4):0.25,(C:1.5,(B:1)#H1:2.5::0.6):1.25);");

julia> getnodeheights_average(inconsistent_net;warn=false)
7-element Vector{Float64}:
 0.0
 1.25
 2.75
 0.25
 2.95
 3.95
 2.75

julia> getnodeheights_majortree(inconsistent_net;warn=false) 
7-element Vector{Float64}:
 0.0
 1.25
 2.75
 0.25
 3.75
 4.75
 2.75

```
