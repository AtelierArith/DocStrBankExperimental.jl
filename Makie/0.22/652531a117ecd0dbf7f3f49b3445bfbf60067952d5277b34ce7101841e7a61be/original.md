```
addmouseevents!(scene, elements...)
```

Returns a `MouseEventHandle` with an observable inside which is triggered by all mouse interactions with the `scene` and optionally restricted to all given plot objects in `elements`.

To react to mouse events, use the onmouse... handlers.

Example:

```julia
mouseevents = addmouseevents!(scene, scatterplot)

onmouseleftclick(mouseevents) do event
    # do something with the mouseevent
end
```
