```
Occurrence
```

This is a sub-type of `AbstractOccurrence`, with the following types:

  * `what` - species name, defaults to `""`
  * `presence` - a boolean to mark the presence of the species, defaults to `true`
  * `where` - a tuple giving the location as longitude,latitude in WGS84, or `missing`, defaults to `missing`
  * `when` - a `DateTime` giving the date of observation, or `missing`, defaults to `missing`

When the interface is properly implemented for any type that is a sub-type of `AbstractOccurrence`, there is an `Occurrence` object can be created directly with *e.g.* `Occurrence(observation)`. There is, similarly, an automatically implemented `convert` method.
