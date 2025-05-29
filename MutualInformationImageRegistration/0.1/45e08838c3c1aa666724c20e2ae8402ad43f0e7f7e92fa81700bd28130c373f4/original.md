```
register!(
    mi::MutualInformationContainer,
    full_image::AbstractArray{T,2},
    fixed::AbstractArray{T,2},
    moving_bbox::AbstractVector{Int},
    max_shift_x::Int,
    max_shift_y::Int,
    buffer::AbstractArray{T,2};
    set_buffer! = (buffer, current_frame, moving_bbox) -> set_buffer!(buffer, current_frame, moving_bbox, max_shift_x, max_shift_y),
    get_buffer_crop = (buffer, moving_bbox, shift_x, shift_y) -> get_buffer_crop(buffer, moving_bbox, shift_x, shift_y, max_shift_x, max_shift_y),
    prefilter_frame_crop! = x -> nothing,
    start_shift_x = 3,
    start_shift_y = 3,
    expand_border = 1,
    expand_increment = 1,
) where {T<:Integer}
```

Calculates the shift that best aligns the `moving_bbox` to the `fixed` image within the `full_image`. At a high level, this attempts to best match the view of `moving_bbox` inside `full_image` to the `fixed` image. This only considers shifts along the x and y axes; no rotation is considered. This function incrementally expands the maximum shift horizon to evaluate as few shifts as possible. At a minimum, all shifts within `± start_shift_x` and `± start_shift_y` are considered. If the optimal shift falls within `expand_border` of the horizon, the horizon will be expanded by `expand_increment` and all new shifts will be evaluated. This process repeats until the optimal shift does not fall within `expand_border` of the horizon, or until the horizon has reached `max_shift_x` and `max_shift_y`.

Adding some padding to `moving_bbox` is a good idea to improve registration stability. E.g. `my_bbox .+ [-10, -10, 10, 10]`. You will need to determine the best padding value for your data.

The parameter `buffer` is required for temporary storage. Generally, you can define `buffer` as `Array{T}(undef, (size(fixed) .+ (MAX_SHIFT * 2))...)`. The buffer must have a size which is at least the size of the `fixed` image expanded by the maximum and minimum x and y shifts on each respective axis. The parameters `set_buffer!` and `get_buffer_crop` are used to write to and read from this buffer, respectively. There is typically no need to change these from their defaults.

The parameter `prefilter_frame_crop!` can be specified if you want to apply image filtering before computing the mutual information between the two images. This function must mutate the image it is given with whatever filtering operation you implement. Also, the `fixed` image must have the filtering pre-applied. See this package's tests for an example.
