```
NoUnits
```

An object that represents "no units", i.e., the units of a unitless number. The type of the object is `Unitful.FreeUnits{(), NoDims}`. It is displayed as an empty string.

Example:

```jldoctest
julia> unit(1.0) == NoUnits
true
```
