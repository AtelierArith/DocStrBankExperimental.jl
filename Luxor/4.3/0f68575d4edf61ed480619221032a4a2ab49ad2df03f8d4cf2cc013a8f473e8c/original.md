```
animate(movie::Movie, scenelist::Vector{Scene};
    creategif = false,
    createmovie = false,
    framerate = 30,
    pathname = "",
    tempdirectory = "")
```

Create all the frames of the `movie``, using the array of scenes defined in`scenelist`.

If `creategif` is `true`, also create an animated GIF (".gif").

If `createmovie` is `true`, also create a movie (".mkv", ".mp4", or ".webm") file.

The file will be stored in the `pathname` keyword argument, or otherwise in a temporary directory.

In suitable environments, a GIF animation is displayed in the Plots window.

### Example

```julia
animate(bang, [
    Scene(bang, backdrop, 0:200),
    Scene(bang, frame1, 0:200, easingfunction=easeinsine)],
    creategif=true,
    pathname="/tmp/animationtest.gif")
```

If you prefer, you can use the FFMPEG.jl package (or the `ffmpeg` executable) separately on the set of still images that have been generated. For example, use code like this:

```julia
using Luxor
using FFMPEG

...

tempdirectory = "/tmp/temp/"

animate(movie, [
        Scene(movie, frame, 1:50)
    ],
    creategif=false,
    tempdirectory=tempdirectory)

FFMPEG.exe(`-r 30 -f image2 -i $(tempdirectory)/%10d.png -c:v libx264 -r 30 -pix_fmt yuv420p -y /tmp/animation.mp4`)

```
