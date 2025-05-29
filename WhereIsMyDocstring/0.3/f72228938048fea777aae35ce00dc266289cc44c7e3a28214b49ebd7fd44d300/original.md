```
@docmatch f
@docmatch f(sig)
@docmatch f module
@docmatch f(sig) module
```

Retrieves all docstrings that would be included in the block

````
```@docs
f
```
````

or

````
```@docs
f(sig)
```
````

The optional argument `module` controls in which module to look for `f`.

#### Example

```
julia> @docmatch sin
2-element Vector{WhereIsMyDocstring.DocStr}:
 Base.sin
  Content:
    sin(x) [...]
  Signature type:
    Tuple{Number}
  Include in ```@docs``` block:
    Base.sin(::Number)
  Source:
   math.jl:490
================================================================================
 Base.sin
  Content:
    sin(A::AbstractMatrix) [...]
  Signature type:
    Tuple{AbstractMatrix{<:Real}}
  Include in ```@docs``` block:
    Base.sin(::AbstractMatrix{<:Real})
  Source:
    /usr/share/julia/stdlib/v1.10/LinearAlgebra/src/dense.jl:956
```
