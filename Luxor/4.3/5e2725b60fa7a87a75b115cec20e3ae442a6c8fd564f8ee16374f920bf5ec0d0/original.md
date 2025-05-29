```
julialogo(;
    action=:fill,
    color=true,
    bodycolor=colorant"black",
    centered=false)
```

Draw the Julia logo. The default action is to fill the logo and use the colors:

```
julialogo()
```

If `color` is `false`, the `bodycolor` color is used for the logo.

The function uses the current drawing state (position, scale, etc).

The `centered` keyword lets you center the logo at its mathematical center, but the optical center might lie somewhere else - it's difficult to position well due to its asymmetric design.

To use the logo as a clipping mask:

```julia
julialogo(action=:clip)
```

(In this case the `color` setting is automatically ignored.)

To obtain a stroked (outlined) version:

```julia
julialogo(action=:path)
sethue("red")
strokepath()
```

TODO Return something more useful than a Boolean.
