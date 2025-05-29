```
clean_ccn(s; max_length=6) -> String
```

Clean the given value `s` and return a `String` in canonical CCN format.

Canonical CCN format is a string of uppercase alphanumeric characters left-padded with zeros to either 6 or 10 characters. Some datasets allow CCNs to have a hyphen in position 2 separating the state code from the facility code, and some store the alphabetical characters in lower case.

# Arguments

  * `s::Union{Integer,AbstractString}` - The value to clean.
  * `max_length::Integer = 6` - The maximum (and pad) length of the CCN. Should be either 6 (for providers) or 10 (for suppliers). Strings shorter than this length will be left-padded with zeros to this length.

# Return

The canonicalized form of `s`.
