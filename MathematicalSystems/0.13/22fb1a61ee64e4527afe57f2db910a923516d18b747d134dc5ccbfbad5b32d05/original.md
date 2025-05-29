```
VaryingInput{UT, VUT<:AbstractVector{UT}} <: AbstractInput
```

Type representing an input that may vary with time.

### Fields

  * `U` – vector of input sets

### Examples

The varying input holds a vector and its length equals the number of elements in the vector. Consider an input given by a vector of rational numbers:

```jldoctest varying_input
julia> v = VaryingInput([-1//2, 1//2])
VaryingInput{Rational{Int64}, Vector{Rational{Int64}}}(Rational{Int64}[-1//2, 1//2])

julia> length(v)
2

julia> eltype(v)
Rational{Int64}
```

Base's `iterate` method receives the input and an integer state and returns the input element and the next iteration state:

```jldoctest varying_input
julia> iterate(v, 1)
(-1//2, 2)

julia> iterate(v, 2)
(1//2, 3)
```

The method `nextinput` receives a varying input and an integer `n` and returns an iterator over the first `n` elements of this input (where `n=1` by default):

```jldoctest varying_input
julia> typeof(nextinput(v))
Base.Iterators.Take{VaryingInput{Rational{Int64}, Vector{Rational{Int64}}}}

julia> collect(nextinput(v, 1))
1-element Vector{Rational{Int64}}:
 -1//2

julia> collect(nextinput(v, 2))
2-element Vector{Rational{Int64}}:
 -1//2
  1//2
```

You can collect the inputs in an array, or equivalently use list comprehension, (or use a `for` loop):

```jldoctest varying_input
julia> collect(v)
2-element Vector{Rational{Int64}}:
 -1//2
  1//2

julia> [3*vi for vi in v]
2-element Vector{Rational{Int64}}:
 -3//2
  3//2
```

Since this input type is finite, querying more elements than its length returns the full vector:

```jldoctest varying_input
julia> collect(nextinput(v, 4))
2-element Vector{Rational{Int64}}:
 -1//2
  1//2
```

To transform a varying input, you can use `map` as in:

```jldoctest varying_input
julia> map(x->3*x, v)
VaryingInput{Rational{Int64}, Vector{Rational{Int64}}}(Rational{Int64}[-3//2, 3//2])
```
