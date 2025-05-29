```
stairs(cmd0::String="", arg1=nothing; step=:post, kwargs...)
```

Plot a stair function. The `step` parameter can take the following values:

`:post` - The default. Lines move first along x for cartesian plots or the parallels for geographic           and then along y or the meridians. `:pre`  - Lines move first along y for cartesian plots or the meridians for geographic           and then along x or the parallels.

Example:

```
x = linspace(0, 4*pi, 50);
stairs(x, sin.(x), show=true)
```
