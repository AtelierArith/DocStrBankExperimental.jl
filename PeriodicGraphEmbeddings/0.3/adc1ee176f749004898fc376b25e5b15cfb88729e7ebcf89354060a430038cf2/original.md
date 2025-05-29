```
find_hall_number(hallsymbol::AbstractString, hm::AbstractString=hallsymbol, it::Integer=0, warnonnotfound=false)
```

Determine the hall number corresponding to the given `hallsymbol`. The Hermann-Mauguin symbol `hm` can alternatively be used, or simply the International Table number of the space group `it` to get the hall number of the standard setting of the group.

Passing an empty string to `hallsymbol` or `hm` or 0 to `it` disregards the argument.

The optional argument `warnonnotfound` specifies whether to print a warning if one of the provided arguments was not reckognized.
