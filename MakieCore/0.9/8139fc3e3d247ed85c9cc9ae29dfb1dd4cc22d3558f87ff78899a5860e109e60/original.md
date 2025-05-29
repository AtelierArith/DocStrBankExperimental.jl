Screen constructors implemented by all backends:

```julia
# Constructor aimed at showing the plot in a window.
Screen(scene::Scene; screen_config...)

# Screen to save a png/jpeg to file or io
Screen(scene::Scene, io::IO, mime; screen_config...)

# Screen that is efficient for `colorbuffer(screen, format)`
Screen(scene::Scene, format::Makie.ImageStorageFormat; screen_config...)
```

Interface implemented by all backends:

```julia
# Needs to be overload:
size(screen) # Size in pixel
empty!(screen) # empties screen state to reuse the screen, or to close it

# Optional
wait(screen) # waits as long window is open

# Provided by Makie:
push_screen!(scene, screen)
```
