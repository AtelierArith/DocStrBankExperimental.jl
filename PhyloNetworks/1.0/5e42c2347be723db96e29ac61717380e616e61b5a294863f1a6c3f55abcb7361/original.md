```
getnodeheights(net, checkpreorder::Bool=true)
getnodeheights!(net, checkpreorder::Bool=true)
```

Vector of node heights, that is: the distance of each node to the root. An error is thrown if the network is not time-consistent. A network is time-consistent if, for any node `v`, all paths from the root to `v` have the same length. (It is sufficient to check this condition at hybrid nodes). Ultrametricity is not assumed: tips need not all be at the same distance from the root. If `checkpreorder=false`, assumes the network has already been preordered with [`preorder!`](@ref).

If a tree edge has a missing length (coded as -1), both functions throw an error. In general, there may be an exponential number of ways to assign tree edge lengths that make the network time-consistent.

`getnodeheights` sends a warning upon finding a missing hybrid edge length, otherwises proceeds as `getnodeheights!` but without modifying the network. `getnodeheights!` will attempt to assign values to missing lengths, for hybrid edges only, so as to make the network time-consistent.

If a hybrid edge `e` has a missing length, `getnodeheights!` proceeds as follows at its child hybrid node `h`:

  * If all of `h`'s parent edges lack a length: the shortest non-negative lengths are assigned to make the network time-consistent at `h`. In particular, one of the partner edges is assigned length 0, and `h` is made as old as possible, that is, as close to the root as possible: the reticulation is "zipped-up".
  * Otherwise: the length of `e` is set to the unique value that makes the network time-consistent at `h`, based on the partner edge's length. If this value is negative, then an error is thrown.

Output: vector of node heights, one per node, in the same order as in `net.vec_node`.

See also: [`istimeconsistent`](@ref) and [`getnodeheights_average`](@ref).

Examples:

```jldoctest
julia> net = readnewick("(((C:1,(A:1)#H1:1.5::0.7):1,(#H1:0.3::0.3,E:2.0):2.2):1.0,O:5.2)root;");

julia> # using PhyloPlots; plot(net, useedgelength=true, showedgelength=true, shownodenumber=true); # to see

julia> nodeheight = getnodeheights(net)
9-element Vector{Float64}:
 0.0
 5.2
 1.0
 3.2
 5.2
 2.0
 3.5
 4.5
 3.0

julia> [node.number => (height, node.name) for (height,node) in zip(nodeheight, net.vec_node)]
9-element Vector{Pair{Int64, Tuple{Float64, String}}}:
 -2 => (0.0, "root")
  5 => (5.2, "O")
 -3 => (1.0, "")
 -6 => (3.2, "")
  4 => (5.2, "E")
 -4 => (2.0, "")
  3 => (3.5, "H1")
  2 => (4.5, "A")
  1 => (3.0, "C")

```
