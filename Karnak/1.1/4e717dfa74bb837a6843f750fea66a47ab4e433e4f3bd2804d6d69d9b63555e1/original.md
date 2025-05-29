Draw a graph `g` using coordinates in `layout` to fit in a Luxor `boundingbox` (defaulting to the current drawing's extent).

Returns a vector of Points, the location of the graph vertices as drawn.

## Keyword arguments

```
boundingbox::BoundingBox        graph fits inside this BB
layout                          Point[] or function
margin                          default 30
edgelist                        draw only these edges

vertexfunction(vtx, coords) ->  draw vertices
edgefunction(edgenumber, edgesrc, edgedest, from, to) -> draw edges
```

`layout`

  * the layout method or coordinates to be used. Examples:

```
layout = squaregrid

layout = shell

layout = vcat(
    [between(O + (-W / 2, -H / 2), O + (-W / 2, H / 2), i) for i in range(0, 1, length=N)], # left
    [between(O + (W / 2, H / 2), O + (W / 2, -H / 2), i) for i in range(0, 1, length=N)] # right
    )

layout = stress

layout = (g) -> spectral(adjacency_matrix(g), dim=2)

layout = shell ∘ adjacency_matrix

layout = (g) -> sfdp(g, Ptype=Float64, dim=2, tol=0.05, C=0.4, K=2)

layout = Shell(nlist=[6:10,]) # inner shell for vertices 6 to 10

layout = squaregrid

the_positions = [(pt.x, pt.y) for pt in randompointarray(BoundingBox(), 50)[1:nv(G)]]
the_weights = rand(1:20, nv(G), nv(G))
layout=Stress(initialpos = the_positions,
    iterations = 30,
    weights = the_weights)

layout = Stress(iterations = 100, weights = M) # M is matrix of weights

layout = Spring(iterations = 200, initialtemp = 2.5)
```

Refer to the NetworkLayout.jl documentation for more.

# Extended help

All keywords:

```plain
 boundingbox                 BoundingBox
 margin                      Number
 layout                      Vector{Point}
                             function from NetworkLayout.jl
                             f(g::Graph)
 edgefunction                f(edgenumber::Int, edgesrc::Int, edgedest::Int, from::Point)
 vertexfunction              f(vtx::Int, coordinates::Vector{Point})
 edgearrows                  :none
                             Boolean - draw end arrow
                             Vector
                             f(edgenumber::Int, edgesrc::Int, edgedest::Int, from::Point)
                             - function overrides edgegaps
 edgecurvature               Float64
 edgedashpatterns            Vector{Vector}[number]
                             Vector{Number}
 edgegaps                    Vector
                             Range
                             Real
                             f(edgenumber::Int, edgesrc::Int, edgedest::Int, from::Point)
 edgelabelcolors             Vector{Colorant}
                             Colorant
 edgelabelfontfaces          Vector{Strings}[edgenumber]
                             String
                             :none
 edgelabelfontsizes          Vector{Number}
                             Number
 edgelabelrotations          Vector{angles}
                             angle::Float64
                             f(edgenumber, edges, edgedest, from, to)
 edgelabels                  Vector
                             range
                             Dict{Int, Int}
                             f(edgenumber, edgesrc, edgedest, from::Point, to::Point)
                               - this function must draw the required text
                             :none
 edgelines                   Vector{Int}
                             range
                             Int
                             f(edgenumber, edgesrc, edgedest, from::Point, to::Point)
 edgelist                    Graphs.EdgeIterator
 edgestrokecolors            Vector{Colorant}[edge::Int]
                             Colorant
                             f(edgenumber, edgesrc, edgedest, from::Point, to::Point)
 edgestrokeweights           Vector{Number}[vtx]
                             range
                             Real
                             f(edgenumber, edgesrc, edgedest, from::Point, to::Point)
 vertexfillcolors            Vector{Colorant}
                             Colorant
                             :none
                             f(vtx::Int)
 vertexlabelfontfaces        Vector{Strings}
                             String
 vertexlabelfontsizes        Vector
                             range
                             Real
                             :none
                             f(vtx::Int, coord::Point[])
                              - function must return a numeric value for fontsize
 vertexlabeloffsetangles     Vector
                             Range
                             Real
 vertexlabeloffsetdistances  Vector
                             range
                             Real
 vertexlabelrotations        Vector
                             range
                             Real
                             :none
 vertexlabels                Vector{String}
                             String
                             range[vtx::Int]
                             :none
                             f(vtx::Int)
                             - this function must return a string
 vertexlabeltextcolors       Vector{Colorant}
                             Colorant
                             f(vtx::Int)
                             :none
 vertexshaperotations        f(vtx::Int)
                             angle::Float64
 vertexshapes                Vector of :circle :square :none
                             range[vtx]
                             :circle :square :none
                             f(vtx::Int)
 vertexshapesizes            Vector{Real}
                             range
                             Real
                             :none
                             f(vtx::Int)
 vertexstrokecolors          Vector
                             Colorant
                             :none
                             f(vtx::Int)
 vertexstrokeweights         Vector
                             range
                             :none
                             f(vtx::Int)
```
