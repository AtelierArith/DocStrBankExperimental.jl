```
first_chunk(d::Declarative; criteria...)
```

Returns the first chunk in memory that matches a set of criteria

# Arguments

  * `d::Declarative`: a declarative memory object

# Keywords

  * `check_value=true`: check slot value
  * `criteria...`: optional keyword arguments corresponding to critiria for matching chunk
