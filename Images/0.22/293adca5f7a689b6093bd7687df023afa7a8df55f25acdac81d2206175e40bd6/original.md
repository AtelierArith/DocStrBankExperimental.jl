```
edges, count = imhist(img, nbins)
edges, count = imhist(img, nbins, minval, maxval)
edges, count = imhist(img, edges)
```

Generates a histogram for the image over nbins spread between `(minval, maxval]`. Color images are automatically converted to grayscale.

# Output

Returns `edges` which is a [`range`](@ref) type that specifies how the  interval `(minval, maxval]` is divided into bins, and an array `count` which records the concomitant bin frequencies. In particular, `count` has the following properties:

  * `count[i+1]` is the number of values `x` that satisfy `edges[i] <= x < edges[i+1]`.
  * `count[1]` is the number satisfying `x < edges[1]`, and
  * `count[end]` is the number satisfying `x >= edges[end]`.
  * `length(count) == length(edges)+1`.

# Details

One can consider a histogram as a piecewise-constant model of a probability density function $f$ [1]. Suppose that $f$ has support on some interval $I = [a,b]$.  Let $m$ be an integer and $a = a_1 < a_2 < \ldots < a_m < a_{m+1} = b$ a sequence of real numbers. Construct a sequence of intervals

$$
I_1 = [a_1,a_2], I_2 = (a_2, a_3], \ldots, I_{m} = (a_m,a_{m+1}]
$$

which partition $I$ into subsets $I_j$ $(j = 1, \ldots, m)$ on which $f$ is constant. These subsets satisfy $I_i \cap I_j = \emptyset, \forall i \neq j$, and are commonly referred to as *bins*. Together they encompass the entire range of data values such that $\sum_j |I_j | = | I |$. Each bin has width $w_j = |I_j| = a_{j+1} - a_j$ and height $h_j$ which is the constant probability density over the region of the bin. Integrating the constant probability density over the width of the bin $w_j$ yields a probability mass of $\pi_j = h_j w_j$ for the bin.

For a sample $x_1, x_2, \ldots, x_N$, let

$$
n_j = \sum_{n = 1}^{N}\mathbf{1}_{(I_j)}(x_n),
\quad \text{where} \quad
\mathbf{1}_{(I_j)}(x) =
\begin{cases}
 1 & \text{if} x \in I_j,\\
 0 & \text{otherwise},
\end{cases},
$$

represents the number of samples falling into the interval $I_j$. An estimate for the probability mass of the $j$th bin is given by the relative frequency $\hat{\pi} = \frac{n_j}{N}$, and the histogram estimator of the probability density function is defined as

$$
\begin{aligned}
\hat{f}_n(x)  & = \sum_{j = 1}^{m}\frac{n_j}{Nw_j} \mathbf{1}_{(I_j)}(x) \\
& = \sum_{j = 1}^{m}\frac{\hat{\pi}_j}{w_j} \mathbf{1}_{(I_j)}(x) \\
& = \sum_{j = 1}^{m}\hat{h}_j \mathbf{1}_{(I_j)}(x).
\end{aligned}
$$

The function $\hat{f}_n(x)$ is a genuine density estimator because $\hat{f}_n(x)  \ge 0$ and

$$
\begin{aligned}
\int_{-\infty}^{\infty}\hat{f}_n(x) \operatorname{d}x & = \sum_{j=1}^{m} \frac{n_j}{Nw_j} w_j \\
& = 1.
\end{aligned}
$$

# Options

Various options for the parameters of this function are described in more detail below.

## Choices for `nbins`

You can specify the number of discrete bins for the histogram.

## Choices for `minval`

You have the option to specify the lower bound of the interval over which the histogram will be computed.  If `minval` is not specified then the minimum value present in the image is taken as the lower bound.

## Choices for `maxval`

You have the option to specify the upper bound of the interval over which the histogram will be computed.  If `maxval` is not specified then the maximum value present in the image is taken as the upper bound.

## Choices for `edges`

If you do not designate the number of bins, nor the lower or upper bound of the interval, then you have the option to directly stipulate how the intervals will be divided by specifying a [`range`](@ref) type.

# Example

Compute the histogram of a grayscale image.

```julia

using TestImages, FileIO, ImageView

img =  testimage("mandril_gray");
edges, counts  = imhist(img,256);
```

Given a color image, compute the hisogram of the red channel.

```julia
img = testimage("mandrill")
r = red(img)
edges, counts  = imhist(r,256);
```

# References

[1] E. Herrholz, "Parsimonious Histograms," Ph.D. dissertation, Inst. of Math. and Comp. Sci., University of Greifswald, Greifswald, Germany, 2011.
