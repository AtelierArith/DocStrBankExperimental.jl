```
SizedArray([TA], T|element, size...) -> Construct{TA}
```

Defines an array with specific size and element.

# Arguments

  * `TA<:AbstractArray{T}`: the target array type, the default is `Array{T, N}`.
  * `T`: the type of elements.
  * `element::Construct{T}`: the construct of elements.
  * `size`: the size of the array.
