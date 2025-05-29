```
see(b::Board, m::Move)::Int
see(b::Board, m::String)::Int
see(b::Board, m::String, movelist::MoveList)::Int
```

Static exchange evaluator.

This function estimates the material gain/loss of a move without doing any search, just looking at the attackers and defenders of the destination square, including X-ray attackers and defenders. It does not consider pins, overloaded pieces, etc., and is therefore only reliable as a very rough guess.

In the `m::String`, `see` internally calls `movesfromsan`, which can be supplied  a pre-allocated `MoveList`in order to save time/space due to unnecessary allocations. If provided, the `movelist` parameter will be passed to `moves`. It is up to the caller to ensure that `movelist` has sufficient capacity.

# Examples

```julia-repl
julia> b = fromfen("8/4k3/8/4p3/8/2BK4/8/q7 w - - 0 1")
Board (8/4k3/8/4p3/8/2BK4/8/q7 w - -):
 -  -  -  -  -  -  -  -
 -  -  -  -  k  -  -  -
 -  -  -  -  -  -  -  -
 -  -  -  -  p  -  -  -
 -  -  -  -  -  -  -  -
 -  -  B  K  -  -  -  -
 -  -  -  -  -  -  -  -
 q  -  -  -  -  -  -  -

julia> see(b, "Bxe5")
-2

julia> b = fromfen("7q/4k1b1/3p4/4n3/8/2BK1N2/4R3/4R3 w - - 0 1")
Board (7q/4k1b1/3p4/4n3/8/2BK1N2/4R3/4R3 w - -):
 -  -  -  -  -  -  -  q
 -  -  -  -  k  -  b  -
 -  -  -  p  -  -  -  -
 -  -  -  -  n  -  -  -
 -  -  -  -  -  -  -  -
 -  -  B  K  -  N  -  -
 -  -  -  -  R  -  -  -
 -  -  -  -  R  -  -  -

julia> see(b, "Nxe5")
1

julia> b = fromfen("7q/4k1b1/3p4/4n3/8/2BK1N2/4R3/4R3 w - - 0 1")
Board (7q/4k1b1/3p4/4n3/8/2BK1N2/4R3/4R3 w - -):
 -  -  -  -  -  -  -  q
 -  -  -  -  k  -  b  -
 -  -  -  p  -  -  -  -
 -  -  -  -  n  -  -  -
 -  -  -  -  -  -  -  -
 -  -  B  K  -  N  -  -
 -  -  -  -  R  -  -  -
 -  -  -  -  R  -  -  -

julia> movelist = MoveList(200)
0-element MoveList

julia> see(b, "Nxe5", movelist)
1
```
