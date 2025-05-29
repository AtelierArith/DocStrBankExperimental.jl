```julia
select_systems(
    systems::Array{Santiago.System},
    n_select::Int64;
    target,
    maximize,
    selection_type,
    techs_include,
    techs_exclude,
    templates_include,
    templates_exclude
) -> Vector{Santiago.System}

```

Select a subset of maximal `n_select` systems. The function aims to  identify systems that have a good target value.

Most system properties can serve as target. The most commonly used one is the `sysappscore`.

## Arguments

  * `n_select::Int` Number of systems to select (if possible)
  * `target = "sysappscore"` value used to rank systems. Can be a string with the name of a system property such as `"sysappscore"`, `"connectivity"`, or `"ntechs"`. For massflow statistics is needs to be a `Pair` of  a product and a massflow statistic such as `("phosphor" => "recovery_ratio")`.
  * `maximize::Bool = true` If `true` the system with the largest `target` values  are selected. If `false` the smallest.
  * `selection_type = "diverse"` Must be either `"diverse"` or  `"ranking"`. If `"ranking"`, the systems with the largest (or smallest) target values are returned. If `"diverse"`, the returned systems have a large (or small) target value but are also as diverse as possible. Diversity is mainly determined by the system templates.

The following optional arguments may be used to restrict the selection further:

  * `techs_include`
  * `techs_exclude`
  * `templates_include`
  * `templates_exclude`

Templates can be abbreviated by giving only the first few characters. *All* matching templates will then be used. This is convinient for interactive use, however, it may lead to confusion! For example, instead of providing the complete template name `"T1 basic template"`, one could use the abbreviation `"T1"`. Note, that this will also match a template with the name `"T11 complicated template"`! So make sure that you abbreviation is unique. In this example one should use at least `"T1 "`.

## Details

As a special functionality, the argument `target` also accepts a `Pair` of `"all"` and a massflow statistic, for example `("all" => "recovery_ratio")`. In this case the *average* of the massflow statistics across all four products is used as target. Note, however, that makes no sense for most massflow statistics!

Note, this function may add properties to the input systems! Any of the following properties may be added if missing:

  * `template`
  * `sysappscore`
  * `ntech`
  * `connectivity`
