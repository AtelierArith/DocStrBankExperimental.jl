```
PermuteDims <: Augmentor.Operation
```

## Description

Permute the dimensions of the given array with the predefined permutation `perm`. This operation is particularly useful if the order of the dimensions needs to be different than the default "julian" layout (described below).

Augmentor expects the given images to be in vertical-major layout for which the colors are encoded in the element type itself. Many deep learning frameworks however require their input in a different order. For example it is not untypical that separate color channels are expected to be encoded in the third dimension.

## Usage

```
PermuteDims(perm)

PermuteDims(perm...)
```

## Arguments

  * **`perm`** : The concrete dimension permutation that should be   used. Has to be specified as a `Vararg{Int}` or as a `NTuple`   of `Int`. The length of `perm` has to match the number of   dimensions of the expected input image to that operation.

## See also

[`SplitChannels`](@ref), [`CombineChannels`](@ref), [`augment`](@ref)

## Examples

```julia-repl
julia> using Augmentor, Colors

julia> A = rand(10, 5, 3) # width=10, height=5, and 3 color channels
10×5×3 Array{Float64,3}:
[...]

julia> img = augment(A, PermuteDims(3,2,1) |> CombineChannels(RGB))
5×10 Array{RGB{Float64},2}:
[...]

julia> img2 = testpattern()
300×400 Array{RGBA{N0f8},2}:
[...]

julia> B = augment(img2, SplitChannels() |> PermuteDims(3,2,1))
400×300×4 Array{N0f8,3}:
[...]
```
