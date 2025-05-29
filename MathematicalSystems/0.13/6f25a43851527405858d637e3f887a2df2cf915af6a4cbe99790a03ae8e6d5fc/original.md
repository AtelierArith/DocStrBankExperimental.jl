```
ConstantInput{UT} <: AbstractInput
```

Type representing an input that remains constant in time.

### Fields

  * `U` – input set

### Examples

The constant input holds a single element and its length is infinite. To access the field `U`, you can use Base's `iterate` given a state, or the method  `nextinput` given the number of desired input elements:

```jldoctest constant_input
julia> c = ConstantInput(-1//2)
ConstantInput{Rational{Int64}}(-1//2)

julia> iterate(c, 1)
(-1//2, nothing)

julia> iterate(c, 2)
(-1//2, nothing)

julia> collect(nextinput(c, 4))
4-element Vector{Rational{Int64}}:
 -1//2
 -1//2
 -1//2
 -1//2
```

The elements of this input are rational numbers:

```jldoctest constant_input
julia> eltype(c)
Rational{Int64}
```

To transform a constant input, you can use `map` as in:

```jldoctest constant_input
julia> map(x->2*x, c)
ConstantInput{Rational{Int64}}(-1//1)
```
