```
WinData, Log = WindowData(Data)
```

Windows the sequence(s) given in `Data` into a collection of subsequnces   of floor(N/5) elements with no overlap, excluding any remainder elements that do not fill the final window. If `Data` is a univariate sequence (vector), `Windata` is a vector of 5 vectors. If `Data` is a set of multivariate sequences (NxM matrix),  each of M columns is treated as a sequence with N elements  and `WinData` is a vector of 5 matrices of size [(floor*N,5), M].  The `Log` dictionary contains information about the windowing process, including: `DataType`      - The type of data sequence passed as `Data`

`DataLength`    - The number of sequence elements in `Data`

`WindowLength`  - The number of elements in each window of `WinData`

`WindowOverlap` - The number of overlapping elements between windows

`TotalWindows`  - The number of windows extracted from `Data`

`Mode`          - Decision to include or exclude any remaining sequence                      elements (`< WinLen`) that do not fill the window.

```
WinData, Log = WindowData(Data::AbstractArray{T} where T<:Real, WinLen::Union{Nothing,Int}=nothing, Overlap::Int=0, Mode::String="exclude")
```

Windows the sequence(s) given in `Data` into a collection of subsequnces using the specified keyword arguments: 

# Arguments:

`WinLen`  - Number of elements in each window, a positive integer (>10)

`Overlap` - Number of overlapping elements between windows, a positive integer (< WinLen)

`Mode`    - Decision to include or exclude any remaining sequence                 elements (< `WinLen`) that do not fill the window,                 a string - either `"include"` or `"exclude"` (default).

# See also  `ExampleData`
