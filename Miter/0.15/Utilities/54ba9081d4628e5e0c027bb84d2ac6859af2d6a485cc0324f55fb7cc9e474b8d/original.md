hpd_heatmap(histogram, probabilities, colors)

Generate a `ColorMatrix` from the histogram that highlights the various probability density regions with the given colors.

`probabilities` should be increasing, between `0` and `1`, and have element *less* than `color`. Both can be iterables.

!!! note
    Methods are only defined when the package `StatsBase` is loaded.

