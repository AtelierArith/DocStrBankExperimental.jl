```
addmousestate!(scene, elements...)
```

Returns an `Observable{MouseState}` which is triggered by all mouse interactions with the `scene` and optionally restricted to all given plot objects in `elements`.

To react to mouse events, use the onmouse... handlers.

Example:

```
mousestate = addmousestate!(scene, scatterplot)

onmouseleftclick(mousestate) do state
    # do something with the mousestate
end
```
