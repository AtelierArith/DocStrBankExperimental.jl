```
CombineChannels <: Augmentor.Operation
```

## Description

Combines the first dimension of a given array into a colorant of type `colortype` using the function `ImageCore.colorview`. The main difference is that a separate color channel is also expected for Gray images.

The shape of the input image has to be appropriate for the given `colortype`, which also means that the separated color channel has to be the first dimension of the array. See [`PermuteDims`](@ref) if that is not the case.

## Usage

```
CombineChannels(colortype)
```

## Arguments

  * **`colortype`** : The color type of the resulting image. Must   be a subtype of `ColorTypes.Colorant` and match the color   channel of the given image.

## See also

[`SplitChannels`](@ref), [`PermuteDims`](@ref), [`augment`](@ref)

## Examples

```julia-repl
julia> using Augmentor, Colors

julia> A = rand(3, 10, 10) # three color channels
3×10×10 Array{Float64,3}:
[...]

julia> augment(A, CombineChannels(RGB))
10×10 Array{RGB{Float64},2}:
[...]

julia> B = rand(1, 10, 10) # singleton color channel
1×10×10 Array{Float64,3}:
[...]

julia> augment(B, CombineChannels(Gray))
10×10 Array{Gray{Float64},2}:
[...]
```
