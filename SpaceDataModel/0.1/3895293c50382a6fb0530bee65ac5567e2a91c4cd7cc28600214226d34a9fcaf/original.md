A variable `v` of a type derived from `AbstractDataVariable` should at least implement:

  * `Base.parent(v)`: the parent array of the variable

Optional:

  * `times(v)`: the timestamps of the variable
  * `units(v)`: the units of the variable
  * `meta(v)`: the metadata of the variable
  * `name(v)`: the name of the variable
