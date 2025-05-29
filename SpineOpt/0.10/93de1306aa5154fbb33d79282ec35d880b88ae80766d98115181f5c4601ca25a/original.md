```
run_spineopt!(m, url_out; <keyword arguments>)
```

Build SpineOpt on the given `m` and solve it; write report(s) to `url_out`. A new Spine database is created at `url_out` if one doesn't exist.

# Arguments

  * `log_level`
  * `optimize`
  * `update_names`
  * `alternative`
  * `write_as_roll`
  * `log_file_path`
  * `resume_file_path`

See [run_spineopt](@ref) for the description of the keyword arguments.
