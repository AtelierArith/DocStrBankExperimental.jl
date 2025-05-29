```
SamePad()
```

Passed as an option to convolutional layers (and friends), this causes the padding to be chosen such that the input and output sizes agree (on the first `N` dimensions, the kernel or window) when `stride==1`. When `stride≠1`, the output size equals `ceil(input_size/stride)`.

See also [`Conv`](@ref), [`MaxPool`](@ref).

# Examples

```jldoctest
julia> xs = rand32(100, 100, 3, 50);  # a batch of images

julia> layer = Conv((2,2), 3 => 7, pad=SamePad())
Conv((2, 2), 3 => 7, pad=(1, 0, 1, 0))  # 91 parameters

julia> layer(xs) |> size  # notice how the dimensions stay the same with this padding
(100, 100, 7, 50)

julia> layer2 = Conv((2,2), 3 => 7)
Conv((2, 2), 3 => 7)  # 91 parameters

julia> layer2(xs) |> size  # the output dimension changes as the padding was not "same"
(99, 99, 7, 50)

julia> layer3 = Conv((5, 5), 3 => 7, stride=2, pad=SamePad())
Conv((5, 5), 3 => 7, pad=2, stride=2)  # 532 parameters

julia> layer3(xs) |> size  # output size = `ceil(input_size/stride)` = 50
(50, 50, 7, 50)
```
