```
prepare_spineopt(url_in; <keyword arguments>)
```

A SpineOpt model from the contents of `url_in` - ready to be passed to [run_spineopt!](@ref). The argument `url_in` must be either a `String` pointing to a valid Spine database, or a `Dict` (e.g. manually created or parsed from a json file).

# Arguments

  * `log_level`
  * `upgrade`
  * `filters`
  * `templates`
  * `mip_solver`
  * `lp_solver`
  * `use_direct_model`
  * `use_model_names`
  * `add_bridges`

See [run_spineopt](@ref) for the description of the keyword arguments.
