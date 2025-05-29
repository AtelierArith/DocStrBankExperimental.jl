```
grdfft(cmd0::String="", arg1=nothing, [arg2=nothing,] kwargs...)
```

Take the 2-D forward Fast Fourier Transform and perform one or more mathematical operations in the frequency domain before transforming back to the space domain.

See full GMT (not the `GMT.jl` one) docs at [`grdfft`](http://docs.generic-mapping-tools.org/latest/grdfft.html)

## Parameters

  * **A** | **azim** :: [Type => Number]    $Arg = azim$

    Take the directional derivative in the azimuth direction measured in degrees CW from north.
  * **C** | **upward** :: [Type => Number]    $Arg = zlevel$

    Upward (for zlevel > 0) or downward (for zlevel < 0) continue the field zlevel meters.
  * **D** | **dfdz** :: [Type => Str or Number]		$Arg = [scale|g]$

    Differentiate the field, i.e., take d(field)/dz. This is equivalent to multiplying by kr in   the frequency domain (kr is radial wave number).
  * **E** | **radial_power** :: [Type => Str]         $Arg = [r|x|y][+w[k]][+n]$

    Estimate power spectrum in the radial direction [r]. Place x or y immediately after E to   compute the spectrum in the x or y direction instead.
  * **F** | **filter** :: [Type => Str or List–        $Arg = [r|x|y]params$

    Filter the data. Place x or y immediately after -F to filter x or y direction only; default is   isotropic [r]. Choose between a cosine-tapered band-pass, a Gaussian band-pass filter, or a   Butterworth band-pass filter.
  * **G** | **save** | **outgrid** | **outfile** :: [Type => Str]

    Output grid file name (or table if **radial_power** is used). Note that this is optional and to   be used only when saving the result directly on disk. Otherwise, just use the G = grdfft(....) form.
  * **I** | **integrate** :: [Type => Str or Number]		$Arg = [scale|g]$

    Integrate the field, i.e., compute integral*over*z (field * dz). This is equivalent to divide   by kr in the frequency domain (kr is radial wave number).
  * **N** | **inquire** :: [Type => Str]         $Arg = [a|f|m|r|s|nx/ny][+a|[+d|h|l][+e|n|m][+twidth][+v][+w[suffix]][+z[p]]$

    Choose or inquire about suitable grid dimensions for FFT and set optional parameters. Control the FFT dimension:
  * **S** | **scale** :: [Type => Number]			$Arg = scale$

    Multiply each element by scale in the space domain (after the frequency domain operations).
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    Select verbosity level, which will send progress reports to stderr.
  * **f** | **geog** | **colinfo** | **coltypes** | **coltype** :: [Type => Str]        $Arg = [i|o]colinfo$

    Specify the data types of input and/or output columns (time or geographical data).
