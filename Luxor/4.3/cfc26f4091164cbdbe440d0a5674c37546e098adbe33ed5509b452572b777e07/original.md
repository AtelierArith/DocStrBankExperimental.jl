```
label(txt::T where T <: AbstractString, alignment::Symbol=:N, pos::Point=O;
    offset=5,
    leader=false,
    leaderoffsets=[0.0, 1.0])
```

Add a text label at a point, positioned relative to that point, for example, `:N` signifies North and places the text directly above that point.

Use one of `:N`, `:S`, `:E`, `:W`, `:NE`, `:SE`, `:SW`, `:NW` to position the label relative to that point.

```julia
label("text")          # positions text at North (above), relative to the origin
label("text", :S)      # positions text at South (below), relative to the origin
label("text", :S, pt)  # positions text South of pt
label("text", :N, pt, offset=20)  # positions text North of pt, offset by 20
```

The default offset is 5 units.

If `leader` is true, draw a line as well.

`leaderoffsts` uses normalized fractions (see `between()`) to specify the gap between the designated points and the start and end of the lines.

TODO: Negative offsets don't give good results.
