```
findmaterial(name::Regex) -> Set{String}
```

Search for materials in the database that match the given regular expression. The method returns a set of paths to the materials that startswith the regular expression. The search is case-insensitive.

# Arguments

  * `name::Regex` : The regular expression that the method will match to the start of the material paths.
