```
FFTIndices{D} <: AbstractArray{FFTIndex{D},D}
```

An iterable object defining a range of CartesianIndices corresponding to FFT indices. This can be used to convert a Cartesian array index to an FFT bin index, or vice versa.

An array of `FFTIndex{D}` objects which correspond to all valid indices of an indexable object.

The outputs use the convention where frequencies at or above the Nyquist frequency for that dimension are negative, matching the output of `FFTW.fftfreq`.

# Examples

```
julia> FFTIndices(4)
4-element FFTIndices{1}:
 FFTIndex(0,)
 FFTIndex(1,)
 FFTIndex(-2,)
 FFTIndex(-1,)

julia> FFTIndices(3, 3)
3×3 FFTIndices{2}:
 FFTIndex(0, 0)   FFTIndex(0, 1)   FFTIndex(0, -1)
 FFTIndex(1, 0)   FFTIndex(1, 1)   FFTIndex(1, -1)
 FFTIndex(-1, 0)  FFTIndex(-1, 1)  FFTIndex(-1, -1)
```
