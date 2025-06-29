```
t = find_threshold(histogram, edges, Balanced())
t = find_threshold(img, Balanced(); nbins = 256)
```

In balanced histogram thresholding, one interprets a  bin as a  physical weight with a mass equal to its occupancy count. The balanced histogram method involves iterating the following three steps: (1) choose the midpoint bin index as a "pivot",  (2) compute the combined weight to the left and right of the pivot bin and (3) remove the leftmost bin if the left side is the heaviest, and the rightmost bin otherwise. The algorithm stops when only a single bin remains. The last bin determines the sought-after threshold.

# Output

Returns a real number `t` in `edges`. The `edges` parameter represents an `AbstractRange` which specifies the intervals associated with the histogram bins.

# Extended help

# Details

Let $f_n$ ($n = 1 \ldots N$) denote the number of observations in the $n$th bin of the histogram. The balanced histogram method constructs a sequence of nested intervals

$$
[1,N] \cap \mathbb{Z} \supset I_2 \supset I_3 \supset \ldots \supset I_{N-1},
$$

where for $k = 2 \ldots N-1$

$$
I_k = \begin{cases}
   I_{k-1} \setminus \{\min \left( I_{k-1} \right) \} &\text{if } \sum_{n = \min \left( I_{k-1} \right)}^{I_m}f_n \gt   \sum_{n =  I_m + 1}^{ \max \left( I_{k-1} \right)} f_n, \\
   I_{k-1} \setminus \{\max \left( I_{k-1} \right) \} &\text{otherwise},
\end{cases}
$$

and $I_m = \lfloor \frac{1}{2}\left(  \min \left( I_{k-1} \right) +  \max \left( I_{k-1} \right) \right) \rfloor$. The final interval $I_{N-1}$ consists of a single element which is the bin index corresponding to the desired threshold.

If one interprets a bin as a physical weight with a mass equal to its occupancy count, then each step of the algorithm can be conceptualised as removing the leftmost or rightmost bin to "balance" the resulting histogram on a pivot. The pivot is defined to be the midpoint between the start and end points of the interval under consideration.

If it turns out that the single element in $I_{N-1}$ equals $1$ or $N$ then the original histogram must have a single peak and the algorithm has failed to find a suitable threshold. In this case the algorithm will fall back to using the `UnimodalRosin` method to select the threshold.

# Arguments

The function arguments are described in more detail below.

## `histogram`

An `AbstractArray` storing the frequency distribution.

## `edges`

An `AbstractRange` specifying how the intervals for the frequency distribution are divided.

# Example

Compute the threshold for the "cameraman" image in the `TestImages` package.

```julia

using TestImages, ImageContrastAdjustment, HistogramThresholding

img = testimage("cameraman")
edges, counts = build_histogram(img, 256)
#=
  The `counts` array stores at index 0 the frequencies that were below the
  first bin edge. Since we are seeking a threshold over the interval
  partitioned by `edges` we need to discard the first bin in `counts`
  so that the dimensions of `edges` and `counts` match.
=#
t = find_threshold(counts[1:end], edges, Balanced())
```

# Reference

1. “BI-LEVEL IMAGE THRESHOLDING - A Fast Method”, Proceedings of the First International Conference on Bio-inspired Systems and Signal Processing, 2008. Available: [10.5220/0001064300700076](https://doi.org/10.5220/0001064300700076)
