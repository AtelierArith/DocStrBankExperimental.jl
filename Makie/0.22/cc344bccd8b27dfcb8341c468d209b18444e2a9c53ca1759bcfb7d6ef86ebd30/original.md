**`Makie.Toggle <: Block`**

A switch with two states.

## Constructors

```julia
Toggle(fig_or_scene; kwargs...)
```

## Examples

```julia
t_horizontal = Toggle(fig[1, 1])
t_vertical = Toggle(fig[2, 1], orientation = :vertical)
t_diagonal = Toggle(fig[3, 1], orientation = pi/4)
on(t_vertical.active) do switch_is_on
    switch_is_on ? println("good morning!") : println("good night")
end
```

**Attributes**

(type `?Makie.Toggle.x` in the REPL for more information about attribute `x`)

`active`, `alignmode`, `buttoncolor`, `cornersegments`, `framecolor_active`, `framecolor_inactive`, `halign`, `height`, `length`, `markersize`, `orientation`, `rimfraction`, `tellheight`, `tellwidth`, `toggleduration`, `valign`, `width`
