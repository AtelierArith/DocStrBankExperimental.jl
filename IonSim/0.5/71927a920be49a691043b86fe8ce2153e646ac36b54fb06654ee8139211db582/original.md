```
sublevelalias!(I::Ion, aliasassignments)
```

`aliasassignments` specifies which aliases should be assigned to which sublevels. There are two options to do this:

  * `aliasassignments` is a Vector of Tuples, with the first element of each being the sublevel (`sublevel::Tuple{String,Real}`) and the second being its assigned alias (`alias::String`)
  * `aliasassignments` is a Dict with the format `alias::String => sublevel::Tuple{String,Real}`

Calls `sublevelalias!(I, sublevel, alias)` for each pair `sublevel, alias`.
