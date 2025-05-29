```
SplitChannels <: Augmentor.Operation
```

## Description

Splits out the color channels of the given image using the function `ImageCore.channelview`. This will effectively create a new array dimension for the colors in the front. In contrast to `ImageCore.channelview` it will also result in a new dimension for gray images.

This operation is mainly useful at the end of a pipeline in combination with [`PermuteDims`](@ref) in order to prepare the image for the training algorithm, which often requires the color channels to be separate.

## Usage

```
SplitChannels()
```

## See also

[`PermuteDims`](@ref), [`CombineChannels`](@ref), [`augment`](@ref)

## Examples

```julia-repl
julia> using Augmentor

julia> img = testpattern()
300×400 Array{RGBA{N0f8},2}:
[...]

julia> augment(img, SplitChannels())
4×300×400 Array{N0f8,3}:
[...]

julia> augment(img, SplitChannels() |> PermuteDims(3,2,1))
400×300×4 Array{N0f8,3}:
[...]
```
