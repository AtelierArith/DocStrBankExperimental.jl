plane(hss::HyperSpectrum, chs::AbstractUnitRange{<:Integer}, normalize=false)

Sums a contiguous range of data channels into an Array. The dimension of the result is one less than the dimension of the HyperSpectrum and is stored as a Float64 to ensure that not information is lost.
