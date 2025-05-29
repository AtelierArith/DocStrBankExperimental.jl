```
GroupMark([ Pairs[] ]; [ named arguments ])
```

Create a group mark. 

Group marks are higher level marks that can contain other marks. They can also   contain all the definitions that the root Vega spec can contain (definitions for  axes, legends, title, etc.).

# Example

```julia
gm = GroupMark(
    signals=[sig1, sig2],
    axes = [ xscale(orient="bottom"), yscale(orient="left") ],
    legends=[ (fill = cscale, title="type", titleFontSize=15) ],
    marks= [ linemark, pointmark ],
)
```
