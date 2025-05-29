```
update_limits!(scene::Scene, limits::Union{Automatic, Rect} = scene.limits[], padding = scene.padding[])
```

This function updates the limits of the `Scene` passed to it based on its data. If an actual limit is set by the theme or its attributes (scene.limits !== automatic), it will not update the limits. Call update_limits!(scene, automatic) for that.
