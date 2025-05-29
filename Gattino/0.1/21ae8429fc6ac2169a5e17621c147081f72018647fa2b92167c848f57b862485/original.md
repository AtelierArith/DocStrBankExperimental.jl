```julia
context(f::Function, width::Int64 = 500, height::Int64 = 720, margin::Pair{Int64, Int64} = 0 => 0) -> ::Context
```

This dispatch of `context` is used to create a 2D `Context`. Margins are provided as a `Pair{Int64, Int64}`, these are the left and top margins  respectively. 

```example
con = context(500, 500) do con::Context
    text!(con, 250, 250, "hello world!")
end
```

Using a combination of `group` and `group!`, we can build layers with specified scaling. For example, the following `Context` draws a shape starting starting at 250px from the left of this 500x500 frame, still consuming  the entire height. For proper scaling, I also made the width 250 less. This will make a scaled window inside of the `Context` that is offset by  250px and 250px wide, whereas our window is not offset at all and has a full width of 500px.

```example
con = context(500, 500) do con::Context
    Gattino.text!(con, 250, 250, "hello world!")
    group(con, 250, 500, 250 => 0) do pointarea
        Gattino.points!(pointarea, [1, 2, 8, 4, 3, 4], 1, 2, 6, 7, 4, 5)
    end
end
```
