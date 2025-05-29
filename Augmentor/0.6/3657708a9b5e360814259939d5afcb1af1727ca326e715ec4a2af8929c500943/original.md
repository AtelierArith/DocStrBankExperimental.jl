```
Reshape <: Augmentor.Operation
```

## Description

Reinterpret the shape of the given array of numbers or colorants. This is useful for example to create singleton-dimensions that deep learning frameworks may need for colorless images, or for converting an image array to a feature vector (and vice versa).

## Usage

```
Reshape(dims)

Reshape(dims...)
```

## Arguments

  * **`dims`** : The new sizes for each dimension of the output   image. Has to be specified as a `Vararg{Int}` or as a   `NTuple` of `Int`.

## See also

[`CombineChannels`](@ref), [`augment`](@ref)

## Examples

```julia-repl
julia> using Augmentor, Colors

julia> A = rand(10,10)
10×10 Array{Float64,2}:
[...]

julia> augment(A, Reshape(10,10,1)) # add trailing singleton dimension
10×10×1 Array{Float64,3}:
[...]
```
