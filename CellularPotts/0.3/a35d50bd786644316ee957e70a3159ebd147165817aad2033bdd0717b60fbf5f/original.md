```
record(
    cpm::CellPotts;
    file = "output.gif",
    steps = 300,
    framerate = 30,
    skip = 1,
    colorby = :type,
    kwargs...)
```

Generates an animation of the Cellular Potts Model.

Change the file type by modifying the file name (e.g. `file = "output.mp4`)
