Construct a band-pass Butterworth filter.

```
Usage: f = bandpassfilter(sze, cutin, cutoff, n)

Arguments:
             sze - A 2 element tuple specifying the size of filter
                   to construct (rows, cols).
   cutin, cutoff - The frequencies defining the band pass 0 - 0.5
               n - The order of the filter, the higher n is the sharper
                   the transition is. (n must be an integer >= 1).
Returns:
               f - Frequency domain filter of size==sze, the frequency
                   origin is at the corners.
```

See also: [`lowpassfilter`](@ref), [`highpassfilter`](@ref), [`highboostfilter`](@ref)
