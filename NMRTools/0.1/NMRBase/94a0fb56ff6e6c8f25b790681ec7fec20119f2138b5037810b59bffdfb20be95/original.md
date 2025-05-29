```
metadata(nmrdata, key)
metadata(nmrdata, dim, key)
metadata(nmrdimension, key)
```

Return the metadata for specified key, or `nothing` if not found. Keys are passed as symbols.

# Examples (spectrum metadata)

  * `:ns`: number of scans
  * `:ds`: number of dummy scans
  * `:rg`: receiver gain
  * `:ndim`: number of dimensions
  * `:title`: spectrum title (contents of title pdata file)
  * `:filename`: spectrum filename
  * `:pulseprogram`: title of pulse program used for acquisition
  * `:experimentfolder`: path to experiment
  * `:noise`: RMS noise level

# Examples (dimension metadata)

  * `:pseudodim`: flag indicating non-frequency domain data
  * `:npoints`: final number of (real) data points in dimension (after extraction)
  * `:td`: number of complex points acquired
  * `:tdzf`: number of complex points when FT executed, including LP and ZF
  * `:bf`: base frequency, in MHz
  * `:sf`: carrier frequency, in MHz
  * `:offsethz`: carrier offset from bf, in Hz
  * `:offsetppm`: carrier offset from bf, in ppm
  * `:swhz`: spectrum width, in Hz
  * `:swppm`: spectrum width, in ppm
  * `:region`: extracted region, expressed as a range in points, otherwise missing
  * `:window`: `WindowFunction` indicating applied apodization
  * `:referenceoffset`: referencing (in ppm) applied to the dimension

See also [`estimatenoise!`](@ref).
