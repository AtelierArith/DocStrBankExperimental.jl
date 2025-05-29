Draw a polar histogram.

If **nbins** is **nothing** or 0, this function computes the number of bins as 3.3 * log10(n) + 1,  with n as the number of elements in x, otherwise the given number of bins is used for the histogram.

:param x: the values to draw as a polar histogram :param num_bins: the number of bins in the polar histogram

**Usage examples:**

.. code-block:: julia

```
julia> # Create example data
julia> x = 2 .* rand(100) .- 1
julia> # Draw the polar histogram
julia> polarhistogram(x, alpha=0.5)
julia> # Draw the polar histogram with 19 bins
julia> polarhistogram(x, nbins=19, alpha=0.5)
```
