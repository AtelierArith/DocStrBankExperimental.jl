filter*array*nospace(array,smooth_t,position=1)

Filters the input, 1-d array. The border value is replicated except if position = 2, in which case it only takes the inner part of the smoothed array.

This function calls under the hood the imfilter function of Images.jl
