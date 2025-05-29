```julia
struct CheapStack{T}
```

Simple stack container.

# Functionalities

The following operations are supported:

  * `isempty`
  * `empty!`
  * `first`
  * `length`
  * `pop!`
  * `push!`

For convenience, `CheapStack` implements [the iteration interface](https://docs.julialang.org/en/v1/manual/interfaces/#man-interface-iteration).

# Fields

  * `store::UnsafeArrays.UnsafeArray{T, 1} where T`
  * `ptr::Base.RefValue{Int64}`
