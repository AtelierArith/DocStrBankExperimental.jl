MutualInformationImageRegistration performs image registration using mutual information.

Here's a complete example on how to use this package:

```jldoctest
using MutualInformationImageRegistration, MutualInformationImageRegistration.FastHistograms, Random

# Create the container used to hold intermediate variables for registration
mi = MutualInformationContainer(
    create_fast_histogram(
        FastHistograms.FixedWidth(),
        FastHistograms.Arithmetic(),
        FastHistograms.NoParallelization(),
        [(0x00, 0xff, 4), (0x00, 0xff, 4)],
    ),
)

# Create the full image that the smaller images to register will be pulled from
full_image = rand(UInt8, 500, 300)
view(full_image, 300:330, 200:220) .= 0xff

# The fixed image is the image that the other images are registered against
fixed = full_image[(300-10):(330+10), (200-10):(220+10)]

# The max shift is the maximum search range
MAX_SHIFT = 11
# Padding is used to grow the bbox for higher quality registration
padding = [-10, -10, 10, 10]

# A buffer is needed to hold intermediate data
buffer = Array{UInt8}(undef, (size(fixed) .+ (MAX_SHIFT * 2))...)

# Introduce a random shift to the moving bbox
expected_x = rand(-5:5)
expected_y = rand(-5:5)

# Register the image given by the bbox (called the moving bbox) against the fixed image
shift, mm, mms = register!(
    mi,
    full_image,
    fixed,
    [300, 200, 330, 220] .+ padding .+ [expected_x, expected_y, expected_x, expected_y],
    MAX_SHIFT,
    MAX_SHIFT,
    buffer,
)

# The shift we get out should be equal and opposite of the shift we applied
shift == (-expected_x, -expected_y)

# output

true
```

Also look at the non-exported traits `NoParallelization` and `SIMD`, which can be used when constructing a `MutualInformationContainer`. `NoParallelization` is the default; other traits can be used to customize how the mutual information computation is run.
