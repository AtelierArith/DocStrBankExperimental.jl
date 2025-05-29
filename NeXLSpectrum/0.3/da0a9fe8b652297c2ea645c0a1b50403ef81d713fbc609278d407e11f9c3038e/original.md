```
HyperSpectrum(arr::Array{T<:Real}, energy::EnergyScale, props::Array{Symbol, Any})

HyperSpectrum(energy::EnergyScale, props::Dict{Symbol,Any}, arr::Array{<:Real}; axisnames = ( "X", "Y", "Z", "A", "B", "C" ), fov = ( 1.0, 1.0, 1.0, 1.0, 1.0, 1.0 ), livetime=)
HyperSpectrum(energy::EnergyScale, props::Dict{Symbol,Any}, arr::AxisArray)
HyperSpectrum(energy::EnergyScale, props::Dict{Symbol,Any}, dims::NTuple{<:Integer}, depth::Int, type::Type{Real}; axisnames = ( "X", "Y", "Z", "A", "B", "C" ), fov = ( 1.0, 1.0, 1.0, 1.0, 1.0, 1.0 )
```

The HyperSpectrum struct represents a multi-dimensional array of Spectrum objects.  The dimension of a HyperSpectrum may be 1 for a traverse or a line-scan, 2 for a spectrum image or >2 for time-series of spectrum images or multi-slice spectrum images.

The first constructor is used to create a HyperSpectrum from a raw Array of data.  The second to construct a HyperSpectrum from another HyperSpectrum or an AxisArray.  The third from a description of the intended contents.

  * `axisnames`: A list of the names by which the axis can be referred
  * `fov`: The full width of the dimension in mm.

HyperSpectra differ from Array{Spectrum} in that the spectra in a HyperSpectrum must share properties like :ProbeCurrent and :BeamEnergy.  However, each pixel can have it's own livetime.  HyperSpectrum objects can refer  to line-scans (1D), spectrum images (2D), slice-and-view (3D), time sequenced images (3D), or higher dimension spectrum images.

Internally, HyperSpectrum reinterpretes an Array{T<:Real, N+1} as an Array{Spectrum{T<:Real},N-1}.

HyperSpectrum objects can be read from a RPL/RAW file (using `readrplraw(filenamebase::AbstractString)`) but can be constructed from any Array{<:Real}.

HyperSpectrum objects can be indexed using the standard Julia array idioms including a single integer index or a CartesianIndex.  For example, to iterate over every spectrum in a HyperSpectrum

```
% Construct a 21 row × 19 column spectrum image with 2048 channels of [0,255].
hs = HyperSpectrum{es, props, (21,19), 2048, UInt8}
for idx in eachindex(hs)
    spec = hs[idx]   % get a Spectrum representing the 2048 channels of data at idx
    spec[22] = 1     % Set the 22nd channel to 1
end
% Indices into a HyperSpectrum are (row, column)
```
