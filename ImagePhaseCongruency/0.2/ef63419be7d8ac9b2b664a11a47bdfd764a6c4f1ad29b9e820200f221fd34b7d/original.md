Construct a high-boost Butterworth filter.

```
Usage: f = highboostfilter(sze, cutoff, n, boost)

Arguments:
         sze - A 2 element tuple specifying the size of filter
               to construct (rows, cols).
      cutoff - The cutoff frequency of the filter 0 - 0.5
           n - The order of the filter, the higher n is the sharper
               the transition is. (n must be an integer >= 1).
       boost - The ratio that high frequency values are boosted
               relative to the low frequency values.  If boost is less
               than one then a 'lowboost' filter is generated
Returns:
           f - Frequency domain filter of size==sze, the frequency
               origin is at the corners.
```

See also: [`lowpassfilter`](@ref), [`highpassfilter`](@ref), [`bandpassfilter`](@ref)
