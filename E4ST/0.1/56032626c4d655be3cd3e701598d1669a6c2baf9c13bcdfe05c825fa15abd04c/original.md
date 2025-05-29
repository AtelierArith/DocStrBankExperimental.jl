```
summarize_post_config() -> summary
```

Summarizes the `post_config`, with columns for:

  * `name` - the property name, i.e. key
  * `required` - whether or not the property is required
  * `default` - default value of this property
  * `description`

| name            | required | default                                                     | description                                                                                                                                                                            |
|:--------------- |:-------- |:----------------------------------------------------------- |:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `sim_paths`     | true     | nothing                                                     | The paths to the desired simulation outputs.                                                                                                                                           |
| `sim_names`     | false    | nothing                                                     | The names of each of the sims. This will get used in post processing.  If none given, `e4st_post` will check the configs in each of the `sim_paths` to see if there is a `name` given. |
| `base_sim_name` | false    |                                                             | The name of the base simulation to use for comparisons.  Used by Modifications                                                                                                         |
| `out_path`      | true     | nothing                                                     | The path to the desired output path for the results of postprocessing.                                                                                                                 |
| `mods`          | false    | OrderedCollections.OrderedDict{Symbol, E4ST.Modification}() | A list of `Modification`s specifying changes for how `e4st_post` runs.  See [`extract_results`](@ref) and [`combine_results`](@ref).                                                   |
