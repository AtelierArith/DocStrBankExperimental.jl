```
list_surveys(client; username=nothing)
list_surveys(client, sink; username=nothing)
```

List all surveys of a LimeSurvey instance. Optional argument `username` can be set to list all surveys belonging to a single user.

Specify a `sink` to parse response into another data structure.

See also: [https://api.limesurvey.org/classes/remotecontrol_handle.html#method_list_surveys](https://api.limesurvey.org/classes/remotecontrol_handle.html#method_list_surveys)

# Examples

```julia-repl
julia> # connect to Limesurvey client c
julia> list_surveys(c)

julia> using DataFrames
julia> list_surveys(c, DataFrame)
```
