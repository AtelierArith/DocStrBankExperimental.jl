@MStructType name fieldnames...

This macro gives a convenient syntax for declaring mutable `StructType`s for reading specific variables from a JSONLines file. Also defines `row[:col]` access for rows of the resulting type.

  * `name`: Name of the `StructType`
  * `fieldnames...`: Names of the variables to be read (must be the same as in the file)
