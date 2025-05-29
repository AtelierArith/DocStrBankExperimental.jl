```
    AdaptiveEqualization <: AbstractHistogramAdjustmentAlgorithm
    AdaptiveEqualization(; nbins = 256, minval = 0, maxval = 1, rblocks = 8, cblocks = 8, clip = 0.1)

    adjust_histogram([T,] img, f::AdaptiveEqualization)
    adjust_histogram!([out,] img, f::AdaptiveEqualization)
```

Performs Contrast Limited Adaptive Histogram Equalisation (CLAHE) on the input image. It differs from ordinary histogram equalization in the respect that the adaptive method computes several histograms, each corresponding to a distinct section of the image, and uses them to redistribute the lightness values of the image. It is therefore suitable for improving the local contrast and enhancing the definitions of edges in each region of an image.

# Details

Histogram equalisation was initially conceived to  improve the contrast in a single-channel grayscale image. The method transforms the distribution of the intensities in an image so that they are as uniform as possible [1]. The natural justification for uniformity is that the image has better contrast  if the intensity levels of an image span a wide range on the intensity scale. As it turns out, the necessary transformation is a mapping based on the cumulative histogram–-see [Equalization](@ref) for more details.

A natural extension of histogram equalisation is to apply the contrast enhancement locally rather than globally [2]. Conceptually, one can imagine that the process involves partitioning the image into a grid of rectangular regions and applying histogram equalisation based on the local CDF of each contextual region. However, to smooth the transition of the pixels from one contextual region to another,  the mapping of a pixel is not necessarily done soley based on the local CDF of its contextual region. Rather, the mapping of a pixel may be interpolated based on the CDF of its contextual region, and the CDFs of the immediate neighbouring regions.

In adaptive histogram equalisation the image $\mathbf{G}$ is partitioned into $P \times Q$ equisized submatrices,

$$
\mathbf{G} =  \begin{bmatrix}
\mathbf{G}_{11} & \mathbf{G}_{12} & \ldots & \mathbf{G}_{1C} \\
\mathbf{G}_{21} & \mathbf{G}_{22} & \ldots & \mathbf{G}_{2C} \\
\vdots & \vdots & \ldots & \vdots \\
\mathbf{G}_{R1} & \mathbf{G}_{R2} & \ldots & \mathbf{G}_{RC} \\
\end{bmatrix}.
$$

For each submatrix $\mathbf{G}_{rc}$, one computes a concomitant CDF, which we shall denote by $T_{rc}(G_{i,j})$. In the most general case, we will require four CDFs

$$
\begin{aligned}
T_1(v)  & \triangleq  T_{rc}(G_{i,j}) \\
T_2(v)  & \triangleq  T_{(r+1)c}(G_{i,j}) \\
T_3(v)  & \triangleq  T_{(r+1)(c+1)}(G_{i,j}) \\
T_4(v)  & \triangleq  T_{r(c+1)}(G_{i,j}).
\end{aligned}
$$

In order to determine which particular CDFs will be used in the interpolation step, it is useful to (i) introduce the function

$$
\Phi(\mathbf{G}_{rc}) = \left(  \phi_{rc},  \phi'_{rc}\right) \triangleq \left(rP - \frac{P}{2}, cQ - \frac{Q}{2} \right),
$$

(ii) form the sequences  $\left(\phi_{11}, \phi_{21}, \ldots, \phi_{R1} \right)$ and $\left(\phi'_{11}, \phi'_{12}, \ldots, \phi'_{1C} \right)$, and (iii) define

$$
\begin{aligned}
t  & \triangleq  \frac{i - \phi_{r1}}{\phi_{(r+1)1} - \phi_{r1} } \\
u  & \triangleq  \frac{j - \phi'_{1c}}{\phi'_{1(c+1)} - \phi'_{1c} }.
\end{aligned}
$$

#### Case I (Interior)

For a  pixel $G_{i,j}$ in the range

$$
P - \frac{P}{2} \le i \le RP - \frac{P}{2}  \quad \text{and}  \quad  Q - \frac{Q}{2} \le j \le CQ - \frac{Q}{2}.
$$

values of $r$ and $c$ are implicitly defined by the solution to the inequalities

$$
\phi_{r1} \le i < \phi_{(r+1)1}  \quad \text{and}  \quad  \phi'_{1c} \le j < \phi'_{1(c+1)}.
$$

The *bilinearly interpolated* transformation that maps an intensity $v$ at location $(i,j)$ in the image to an intensity $v'$ is given by [3]

$$
v' \triangleq \bar{T}(v)  = (1-t) (1-u)T_1(G_{i,j}) + t(1-u)T_2(G_{i,j}) + tuT_3(G_{i,j}) +(1-t)uT_4(G_{i,j}).
$$

#### Case II (Vertical Border)

For a  pixel $G_{i,j}$ in the range

$$
P - \frac{P}{2} \le i \le RP - \frac{P}{2}  \quad \text{and}  \quad  1 \le j < Q - \frac{Q}{2}  \; \cup \;   CQ - \frac{Q}{2} < j \le CQ,
$$

$r$ is implicitly defined by the solution to the inequality $\phi_{r1} \le i < \phi_{(r+1)1}$, while

$$
c = \begin{cases}
   1, & \text{if }  \quad  1 \le j < Q - \frac{Q}{2}  \\
   C, & \text{if } \quad   CQ - \frac{Q}{2} < j \le CQ.
\end{cases}
$$

The *linearly interpolated* transformation that maps an intensity $v$ at location $(i,j)$ in the image to an intensity $v'$ is given by

$$
v' \triangleq \bar{T}(v)  = (1-t)T_1(G_{i,j}) + tT_2(G_{i,j}).
$$

#### Case III (Horizontal Border)

For a  pixel $G_{i,j}$ in the range

$$
1 \le i < P - \frac{P}{2}  \;\cup \;   RP - \frac{P}{2} < i \le RP    \quad \text{and}  \quad  Q - \frac{Q}{2} \le j \le CQ - \frac{Q}{2},
$$

$c$ is implicitly defined by the solution to the inequality $\phi'_{1c} \le j < \phi'_{1(c+1)}$, while

$$
r = \begin{cases}
   1, & \text{if }  \quad  1 \le i < P - \frac{P}{2}  \\
   R, & \text{if } \quad   RP - \frac{P}{2} < i \le RP .
\end{cases}
$$

The *linearly interpolated* transformation that maps an intensity $v$ at location $(i,j)$ in the image to an intensity $v'$ is given by

$$
v' \triangleq \bar{T}(v)  = (1-u)T_1(G_{i,j}) + uT_4(G_{i,j}).
$$

#### Case IV (Corners)

For a  pixel $G_{i,j}$ in the range

$$
1 \le i < \frac{P}{2}  \;\cup \; RP - \frac{P}{2} < i \le RP   \quad \text{and}  \quad  1 \le j < CQ -  \frac{Q}{2} \; \cup \;   CQ - \frac{Q}{2} < j \le CQ ,
$$

we have

$$
r = \begin{cases}
   1, & \text{if }  \quad  1 \le i < P - \frac{P}{2}  \\
   R, & \text{if } \quad   RP - \frac{P}{2} < i \le RP
\end{cases}
 \quad \text{and}  \quad
c = \begin{cases}
   1, & \text{if }  \quad  1 \le j < Q - \frac{Q}{2}  \\
   C, & \text{if } \quad   CQ - \frac{Q}{2} < j \le CQ.
\end{cases}
$$

The transformation that maps an intensity $v$ at location $(i,j)$ in the image to an intensity $v'$ is given by

$$
v' \triangleq \bar{T}(v)  = T_1(G_{i,j}).
$$

## Limiting Contrast

An unfortunate side-effect of contrast enhancement is that it has a tendency to amplify the level of noise in an image, especially when the magnitude of the contrast enhancement is very high. The magnitude of contrast enhancement is associated with the gradient of $T(\cdot)$, because the  gradient determines the extent to which consecutive input intensities are stretched across the grey-level spectrum. One can diminish the level of noise amplification by limiting the magnitude of the contrast enhancement, that is, by limiting the magnitude of the gradient.

Since the derivative of $T(\cdot)$ is the empirical density $\hat{f}_{G}$, the slope of the mapping function at any input intensity is proportional to the height of the histogram  $\hat{f}_{G}$ at that intensity.  Therefore, limiting the slope of the local mapping function is equivalent to clipping the height of the histogram. A detailed description of the  implementation  details of the clipping process can be found in [2].

# Options

Various options for the parameters of this function are described in more detail below.

## Choices for `img`

The function can handle a variety of input types. The returned image depends on the input type.

For coloured images, the input is converted to [YIQ](https://en.wikipedia.org/wiki/YIQ) type and the Y channel is equalised. This is the combined with the I and Q channels and the resulting image converted to the same type as the input.

## Choices for `nbins` in `AdaptiveEqualization`

You can specify the total number of bins in the histogram of each local region.

## Choices for `rblocks` and `cblocks` in `AdaptiveEqualization`

The `rblocks` and `cblocks` specify the number of blocks to divide the input image into in each direction. By default both values are set to eight.

## Choices for `clip` in `AdaptiveEqualization`

The `clip` parameter must be a value between 0 and 1. It defines an implicit threshold at which a histogram is clipped. Counts that exceed the threshold are redistributed as equally as possible so that no bin exceeds the threshold limit. A value of zero means no clipping, whereas a value of one sets the threshold at the smallest feasible bin limit. A bin limit is feasible if all bin counts can be redistributed such that no bin count exceeds the limit. In practice, a `clip` value of zero corresponds to maximal contrast enhancement, whereas a `clip` value of one corredponds to minimal contrast enhancement. The default value is `0.1`.

## Choices for `minval` and `maxval` in `AdaptiveEqualization`

If `minval` and `maxval` are specified then intensities are equalized to the range [`minval`, `maxval`]. The default values are 0 and 1.

# Example

```julia

using TestImages, FileIO, ImageView

img =  testimage("mandril_gray")
imgeq = adjust_histogram(img, AdaptiveEqualization(nbins = 256, rblocks = 4, cblocks = 4, clip = 0.2))

imshow(img)
imshow(imgeq)
```

# References

1. R. C. Gonzalez and R. E. Woods. *Digital Image Processing (3rd Edition)*.  Upper Saddle River, NJ, USA: Prentice-Hall,  2006.
2. S. M. Pizer, E. P. Amburn, J. D. Austin, R. Cromartie, A. Geselowitz, T. Greer, B. ter Haar Romeny, J. B. Zimmerman and K. Zuiderveld “Adaptive histogram equalization and its variations,” *Computer Vision, Graphics, and Image Processing*, vol. 38, no. 1, p. 99, Apr. 1987. [10.1016/S0734-189X(87)80186-X](https://doi.org/10.1016/s0734-189x(87)80156-1)
3. W. H. Press, S. A. Teukolsky, W. T. Vetterling, and B. P. Flannery.  *Numerical Recipes: The Art of Scientific Computing (3rd Edition)*. New York, NY, USA: Cambridge University Press, 2007.
