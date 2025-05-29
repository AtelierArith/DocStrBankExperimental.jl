The `Movie` and `Scene` types and the `animate()` function are designed to help you create the frames that can be used to make an animated GIF or movie.

1. Provide width, height, title, and optionally a frame range to the Movie constructor:

    ```julia
    demo = Movie(400, 400, "test", 1:500)
    ```
2. Define one or more scenes and scene-drawing functions.
3. Run the `animate()` function, calling those scenes.

Example

```julia
bang = Movie(400, 100, "bang")

backdrop(scene, framenumber) =  background("black")

function frame1(scene, framenumber)
    background("white")
    sethue("black")
    eased_n = scene.easingfunction(framenumber, 0, 1, scene.framerange.stop)
    circle(O, 40 * eased_n, :fill)
end

animate(bang, [
    Scene(bang, backdrop, 0:200),
    Scene(bang, frame1, 0:200, easingfunction=easeinsine)],
    creategif=true,
    pathname="/tmp/animationtest.gif")
```
