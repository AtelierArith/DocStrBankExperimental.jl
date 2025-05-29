```
create_franklin_note(note::Note; date_format::String = "U d y")
```

Transform a generic `Note` into a `[FranklinNote](@ref)` data structure with special metadata from `Note` content.

# Arguments

  * `note`: a `Note` object that will be used for conversion

# Keyword Arguments

  * `date_format`: a `String` that accepts a date format; default "U d y" (see: `Dates.format` for options)

# Return

  * A newly prepared `FranklinNote` object
