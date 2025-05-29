```
pprof([data, [lidict]];
        web = true, webhost = "localhost", webport = 57599,
        out = "profile.pb.gz", from_c = true, full_signatures = true, drop_frames = "",
        keep_frames = "", ui_relative_percentages = true, sampling_delay = nothing,
     )
pprof(FlameGraphs.flamegraph(); kwargs...)
```

Fetches the collected `Profile` data, exports to the `pprof` format, and (optionally) opens a `pprof` web-server for interactively viewing the results.

If `web=true`, the web-server is opened in the background. Re-running `pprof()` will refresh the web-server to use the new output.

If you manually edit the output file, `PProf.refresh()` will refresh the server without overwriting the output file. `PProf.kill()` will kill the server.

You can also use `PProf.refresh(file="...")` to open a new file in the server.

# Arguments:

  * `data::Vector{UInt}`: The data provided by `Profile.retrieve()` [optional].
  * `lidict::Dict`: The lookup dictionary provided by `Profile.retrieve()` [optional].

      * Note that you need both the `data` and the `lidict` returned from `Profile.retrieve()` in order to export profiling data between julia processes.
  * `flamegraph`: PProf also accepts profile data passed as a `FlameGraphs.jl` graph object.

# Keyword Arguments

  * `sampling_delay::UInt64`: The period between samples in nanoseconds [optional].
  * `web::Bool`: Whether to launch the `go tool pprof` interactive webserver for viewing results.
  * `webhost::AbstractString`: If using `web`, which host to launch the webserver on.
  * `webport::Integer`: If using `web`, which port to launch the webserver on.
  * `out::String`: Filename for output.
  * `from_c::Bool`: If `false`, exclude frames that come from from_c. Defaults to `true`.
  * `full_signatures::Bool`: If `true`, methods are printed as signatures with full argument                          types. If `false`, as only names. E.g. `eval(::Module, ::Any)` vs `eval`.
  * `drop_frames`: frames with function_name fully matching regexp string will be dropped from the samples,                along with their successors.
  * `keep_frames`: frames with function*name fully matching regexp string will be kept, even if it matches drop*functions.
  * `ui_relative_percentages`: Passes `-relative_percentages` to pprof. Causes nodes ignored/hidden through the web UI to be ignored from totals when computing percentages.
