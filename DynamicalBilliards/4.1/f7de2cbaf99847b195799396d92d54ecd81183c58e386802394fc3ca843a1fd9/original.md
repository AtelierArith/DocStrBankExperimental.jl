```
bdplot(x; kwargs...) → fig, ax
bdplot!(ax::Axis, x; kwargs...)
```

Plot an object `x` from `DynamicalBilliards` into a given axis (or a new figure). `x` can be an obstacle, a particle, a vector of particles, or a billiard.

```
bdplot!(ax,::Axis, o::Obstacle; kwargs...)
```

Keywords are propagated to `lines!` or `poly!`. Functions `obfill, obcolor, obls, oblw` (not exported) decide global defaults for linecolor, fillcolor, linestyle, linewidth, when plotting obstacles.

```
bdplot!(ax,::Axis, bd::Billiard; clean = true, kwargs...)
```

If `clean = true`, all axis elements are removed and an equal aspect ratio is establised. Other keywords are propagated to the obstacle plots.

```
bdplot!(ax,::Axis, bd::Billiard, xmin, xmax, ymin, ymax; kwargs...)
```

This call signature plots periodic billiards: it plots `bd` along its periodic vectors so that it fills the total amount of space specified by `xmin, xmax, ymin, ymax`.

```
bdplot!(ax,::Axis, ps::Vector{<:AbstractParticle}; kwargs...)
```

Plot particles as a scatter plot (positions) and a quiver plot (velocities). Keywords `particle_size = 5, velocity_size = 0.05` set the size of plotted particles. Keyword `colors = JULIADYNAMICS_CMAP` decides the color of the particles, and can be either a colormap or a vector of colors with equal length to `ps`. The rest of the keywords are propagated to the scatter plot of the particles.
