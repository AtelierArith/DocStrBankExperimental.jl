```
tickline(startpos, finishpos;
    startnumber         = 0,
    finishnumber        = 1,
    major               = 1,
    minor               = 0,
    major_tick_function = nothing,
    minor_tick_function = nothing,
    rounding            = 2,
    axis                = true, # draw the line?
    log                 = false,
    vertices            = false # just return the points
    )
```

Draw a line with ticks. `major` is the number of ticks required between the start and finish point. So `1` divides the line in half. `minor` is the number of ticks between each major tick.

## Examples

```julia
tickline(Point(0, 0), Point(100, 0))
tickline(Point(0, 0), Point(100, 0), major = 4)
majorticks, minorticks = tickline(Point(0, 0), Point(100, 0), axis=false)
```

## Custom ticks

Supply functions to make custom ticks. Custom tick functions should have arguments as follows:

```julia
function mtick(n, pos;
        startnumber         = 0,
        finishnumber        = 1,
        nticks = 1)
        ...
```

and

```julia
function mntick(n, pos;
        startnumber        = 0,
        finishnumber       = 1,
        nticks             = 1,
        majorticklocations = [])
        ...
```

For example:

```julia
tickline(O - (300, 0), Point(300, 0),
    startnumber  = -10,
    finishnumber = 10,
    minor        = 0,
    major        = 4,
    axis         = false,
    major_tick_function = (n, pos;
        startnumber=30, finishnumber=40, nticks=10) -> begin
        @layer begin
            translate(pos)
            ticklength = get_fontsize()
            line(O, O + polar(ticklength, 3π/2), :stroke)
            k = rescale(n, 0, nticks - 1, startnumber, finishnumber)
            ticklength = get_fontsize() * 1.3
            text("$(round(k, digits=2))",
                O + (0, ticklength),
                halign=:center,
                valign=:middle,
                angle = -getrotation())
        end
    end)
```
