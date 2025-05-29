```
highlight!(
    q::AbstractQuery; fields::AbstractArray=nothing, tags::AbstractArray=nothing
)

Highlighting will highlight the found term (and its variants) with a user-defined tag. 
This may be used to display the matched text in a different typeface using a markup 
language, or to otherwise make the text appear differently.
```

# Arguments

  * `q::AbstractQuery`: Query object.

# KeyWords

  * `fields::AbstractArray`: List of fields
  * `tags::AbstractArray`: User Tag objects.
