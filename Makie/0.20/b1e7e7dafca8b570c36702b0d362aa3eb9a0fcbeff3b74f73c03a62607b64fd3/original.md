```
autolimits!(ax::PolarAxis[, unlock_zoom = true])
```

Calling this tells the PolarAxis to derive limits freely from the plotted data, which allows rmin > 0 and thetalimits spanning less than a full circle. If `unlock_zoom = true` this also unlocks zooming in r and theta direction and allows for translations in r direction.
