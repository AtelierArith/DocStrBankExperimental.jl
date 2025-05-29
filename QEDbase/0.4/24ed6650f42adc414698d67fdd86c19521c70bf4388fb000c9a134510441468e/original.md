```
AbstractCoordinateTransformation
```

Abstract base type for coordinate transformations supposed to be acting on four-momenta. Every subtype of `trafo::AbstractCoordinateTransformation` should implement the following interface functions:

  * `QEDbase._transform(trafo,p)`: transforms `p`
  * `Base.inv(trafo)`: returns the inverted transform

## Example

Implementing the interface by defining the interface functions:

```jldoctest trafo_interface
julia> using QEDbase

julia> struct TestTrafo{T} <: AbstractCoordinateTransformation
           a::T
       end

julia> QEDbase._transform(trafo::TestTrafo,p) = trafo.a*p

julia> Base.inv(trafo::TestTrafo) = TestTrafo(inv(trafo.a))

```

The `TestTrafo` can then be used to transform four-momenta:

```julia
julia> trafo = TestTrafo(2.0)
TestTrafo{Float64}(2.0)

julia> p = SFourMomentum(4,3,2,1)
4-element SFourMomentum with indices SOneTo(4):
 4.0
 3.0
 2.0
 1.0

julia> trafo(p) # multiply every component with 2.0
4-element SFourMomentum with indices SOneTo(4):
 8.0
 6.0
 4.0
 2.0

julia> inv(trafo)(p) # divide every component by 2.0
4-element SFourMomentum with indices SOneTo(4):
 2.0
 1.5
 1.0
 0.5
```
