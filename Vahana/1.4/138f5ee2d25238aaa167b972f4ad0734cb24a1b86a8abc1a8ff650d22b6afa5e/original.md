```
create_logger!(sim::Simulation, [debug = false, name = sim.name; overwrite = sim.overwrite_file])
```

The canonical way to create log files for a simulation is by setting the logging keyword of [`create_simulation`](@ref) to true. But sometime it can be useful to control this manually, e.g. after a call to [`copy_simulation`](@ref).

When also `debug` is set to true, the log file contains more details and the stream will be flushed after each write.

The `filename` argument can be used to specify a filename other than `sim.filename`. If `overwrite` is true, existing files with this name will be overwritten. If it is false, the filename is automatically extended by an increasing 6-digit number, so that existing files are not overwritten.

The files are always created in a `log` subfolder, and this one will be create in the current working directory.
