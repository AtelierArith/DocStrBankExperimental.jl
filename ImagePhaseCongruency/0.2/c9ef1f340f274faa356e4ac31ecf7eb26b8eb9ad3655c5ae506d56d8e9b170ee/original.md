Construct a low-pass Butterworth filter.

```
Usage: f = lowpassfilter(sze, cutoff, n)

where: sze    is a two element tuple specifying the size of filter
              to construct (rows, cols).
       cutoff is the cutoff frequency of the filter 0 - 0.5
       n      is the order of the filter, the higher n is the sharper
              the transition is. (n must be an integer >= 1).
              Note that n is doubled so that it is always an even integer.

                      1
      f =    --------------------
                              2n
              1.0 + (w/cutoff)
```

The frequency origin of the returned filter is at the corners.

See also: [`highpassfilter`](@ref), [`highboostfilter`](@ref), [`bandpassfilter`](@ref)
