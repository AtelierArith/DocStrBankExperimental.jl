```julia
write_to_json(
    file::String,
    sol::HallThruster.Solution;
    average_start_time,
    save_time_resolved
)

```

Write `sol` to `file`, if `file` is a JSON file.

## Mandatory arguments

  * `file`: the file to which we write the solution
  * `sol`: the `Solution` object to be written

## Optional keyword args

  * `average_start_time` = -1: the time at which averaging begins. If < 0, no averaged output is written.
  * `save_time_resolved` = true: Whether to save all frames of the simulation. If `false`, no time-resolved output is written.
