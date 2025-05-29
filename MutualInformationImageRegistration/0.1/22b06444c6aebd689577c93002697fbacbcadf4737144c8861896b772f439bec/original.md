```
register!(
    mi::MutualInformationContainer,
    full_image::AbstractArray{T,2},
    fixed::AbstractArray{T,2},
    moving_bbox::AbstractVector{Int},
    range_x::AbstractVector{Int},
    range_y::AbstractVector{Int},
    buffer::AbstractArray{T,2},
    prev_mis::Union{Missing,AbstractArray{Float32,2}};
    set_buffer! = (buffer, current_frame, moving_bbox) -> set_buffer!(buffer, current_frame, moving_bbox, maximum(range_x), maximum(range_y)),
    get_buffer_crop = (buffer, moving_bbox, shift_x, shift_y) -> get_buffer_crop(buffer, moving_bbox, shift_x, shift_y, maximum(range_x), maximum(range_y)),
    prefilter_frame_crop! = x -> nothing,
) where {T<:Integer}
```

Calculates the shift that best aligns the `moving_bbox` to the `fixed` image within the `full_image`. At a high level, this attempts to best match the view of `moving_bbox` inside `full_image` to the `fixed` image. This only considers shifts along the x and y axes; no rotation is considered. All combinations of shifts within `range_x` and `range_y` are considered.

Adding some padding to `moving_bbox` is a good idea to improve registration stability. E.g. `my_bbox .+ [-10, -10, 10, 10]`. You will need to determine the best padding value for your data.

The parameter `buffer` is required for temporary storage between calls to this function because it is assumed that you will call this function in a loop to register many similar images. Generally, you can define `buffer` as `Array{T}(undef, (size(fixed) .+ (MAX_SHIFT * 2))...)`. The buffer must have a size which is at least the size of the `fixed` image expanded by the maximum and minimum x and y shifts on each respective axis. The parameters `set_buffer!` and `get_buffer_crop` are used to write to and read from this buffer, respectively. There is typically no need to change these from their defaults.

The parameter `prev_mis` is used to memoize the mutual information calculations if this function is being called "incrementally" with an expanding shift horizon. If you are calling this function directly (and not in a loop to gradually expand a maximum shift horizon), you should set this to `missing`, which would cause all combinations of shifts within `range_x` and `range_y` to be considered.

The parameter `prefilter_frame_crop!` can be specified if you want to apply image filtering before computing the mutual information between the two images. This function must mutate the image it is given with whatever filtering operation you implement. Also, the `fixed` image must have the filtering pre-applied. See this package's tests for an example.
