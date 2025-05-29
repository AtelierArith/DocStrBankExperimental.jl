```
Scene(movie, function, range;
    easingfunction=easinoutquad,
    optarg=nothing)
```

Use the Scene() constructor function to create a scene. Supply a movie, a function to generate the scene, and a range of frames. Optionally you can supply an easing function, and other information, in `optarg`, which can be accessed as `scene.opts`.

### Example

```julia
function initial(scene, framenumber)
    balls = scene.opts
    ...
end

animate(poolmovie, [
    Scene(poolmovie, initial, optarg=balls, 1:20),
    ...
    ])
```

To use an easing function inside the frame-generating function, you can create a normalized value with, for example:

```julia
eased_n = scene.easingfunction(framenumber, 0, 1, scene.framerange.stop)
```

Or, if the scene doesn't start at frame 1, calculate normalized easing function like this:

```julia
eased_n = scene.easingfunction(framenumber - scene.framerange.start,
    0, 1, scene.framerange.stop - scene.framerange.start)
```
