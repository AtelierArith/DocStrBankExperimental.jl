```
hist_equalised_img = clahe(img, nbins, xblocks = 8, yblocks = 8, clip = 3)

```

Performs Contrast Limited Adaptive Histogram Equalisation (CLAHE) on the input image. It differs from ordinary histogram equalization in the respect that the adaptive method computes several histograms, each corresponding to a distinct section of the image, and uses them to redistribute the lightness values of the image. It is therefore suitable for improving the local contrast and enhancing the definitions of edges in each region of an image.

# Details

Histogram equalisation was initially conceived to  improve the contrast in a single-channel grayscale image. The method transforms the distribution of the intensities in an image so that they are as uniform as possible [1]. The natural justification for uniformity is that the image has better contrast  if the intensity levels of an image span a wide range on the intensity scale. As it turns out, the necessary transformation is a mapping based on the cumulative histogram–-see [histeq](@ref) for more details.

A natural extension of histogram equalisation is to apply the contrast enhancement locally rather than globally [2]. Conceptually, one can imagine that the process involves partitioning the image into a grid of rectangular regions and applying histogram equalisation based on the local CDF of each contextual region. However, to smooth the transition of the pixels from one contextual region to another,  the mapping of a pixel is not done soley based on the local CDF of its contextual region. Rather, the mapping of a pixel is a bilinear blend based on the CDF of its contextual region, and the CDFs of the immediate neighbouring regions.

In adaptive histogram equalisation the image $\mathbf{G}$ is partitioned into $P \times Q$ equisized submatrices,

$$
\mathbf{G} =  \begin{bmatrix}
\mathbf{G}_{11} & \mathbf{G}_{12} & \ldots & \mathbf{G}_{1C} \\
\mathbf{G}_{21} & \mathbf{G}_{22} & \ldots & \mathbf{G}_{2C} \\
\vdots & \vdots & \ldots & \vdots \\
\mathbf{G}_{R1} & \mathbf{G}_{R2} & \ldots & \mathbf{G}_{RC} \\
\end{bmatrix}.
$$

For each submatrix $\mathbf{G}_{rc}$, one computes a concomitant CDF, which we shall denote by $T_{rc}(G_{i,j})$. In order to determine which CDFs will be used in the bilinear interpolation step, it is useful to  introduce the function

$$
\Phi(\mathbf{G}_{rc}) = \left(  \phi_{rc},  \phi'_{rc}\right) \triangleq \left(\frac{rP}{2}, \frac{cQ}{2} \right)
$$

and to form the sequences  $\left(\phi_{11}, \phi_{21}, \ldots, \phi_{R1} \right)$ and $\left(\phi'_{11}, \phi'_{12}, \ldots, \phi'_{1C} \right)$. For a given pixel $G_{i,j}(\omega)$, values of $r$ and $c$ are implicitly defined by the solution to the inequalities

$$
\phi_{r1} \le i \le \phi_{(r+1)1}  \quad \text{and}  \quad  \phi'_{1c} \le j \le \phi'_{1(c+1)}.
$$

With $r$ and $c$ appropriately defined, the requisite CDFs are given by

$$
\begin{aligned}
T_1(v)  & \triangleq  T_{rc}(G_{i,j}) \\
T_2(v)  & \triangleq  T_{(r+1)c}(G_{i,j}) \\
T_3(v)  & \triangleq  T_{(r+1)(c+1)}(G_{i,j}) \\
T_4(v)  & \triangleq  T_{r(c+1)}(G_{i,j}).
\end{aligned}
$$

Finally, with

$$
\begin{aligned}
t  & \triangleq  \frac{i - \phi_{r1}}{\phi_{(r+1)1} - \phi_{r1} } \\
u  & \triangleq  \frac{j - \phi'_{1c}}{\phi'_{1(c+1)} - \phi'_{1c} },
\end{aligned}
$$

the bilinear interpolated transformation that maps an intensity $v$ at location $(i,j)$ in the image to an intensity $v'$ is given by [3]

$$
v' \triangleq \bar{T}(v)  = (1-t) (1-u)T_1(G_{i,j}) + t(1-u)T_2(G_{i,j}) + tuT_3(G_{i,j}) +(1-t)uT_4(G_{i,j}).
$$

An unfortunate side-effect of contrast enhancement is that it has a tendency to amplify the level of noise in an image, especially when the magnitude of the contrast enhancement is very high. The magnitude of contrast enhancement is associated with the gradient of $T(\cdot)$, because the  gradient determines the extent to which consecutive input intensities are stretched across the grey-level spectrum. One can diminish the level of noise amplification by limiting the magnitude of the contrast enhancement, that is, by limiting the magnitude of the gradient.

Since the derivative of $T(\cdot)$ is the empirical density $\hat{f}_{G}$, the slope of the mapping function at any input intensity is proportional to the height of the histogram  $\hat{f}_{G}$ at that intensity.  Therefore, limiting the slope of the local mapping function is equivalent to clipping the height of the histogram. A detailed description of the  implementation  details of the clipping process can be found in [2].

# Options

Various options for the parameters of this function are described in more detail below.

## Choices for `img`

The `clahe` function can handle a variety of input types. The returned image depends on the input type. If the input is an `Image` then the resulting image is of the same type and has the same properties.

For coloured images, the input is converted to [YIQ](https://en.wikipedia.org/wiki/YIQ) type and the Y channel is equalised. This is the combined with the I and Q channels and the resulting image converted to the same type as the input.

## Choices for `nbins`

You can specify the total number of bins in the histogram of each local region.

## Choices for `xblocks` and `yblocks`

The `xblocks` and `yblocks` specify the number of blocks to divide the input image into in each direction. By default both values are set to eight.

## Choices for `clip`

The `clip` parameter specifies the value at which the histogram is clipped.  The default value is three. The excess in the histogram bins with value exceeding `clip` is redistributed among the other bins.

# Example

```julia

using Images, TestImages, ImageView

img =  testimage("mandril_gray")
imgeq = clahe(img,256, xblocks = 50, yblocks = 50)

imshow(img)
imshow(imgeq)
```

# References

1. R. C. Gonzalez and R. E. Woods. *Digital Image Processing (3rd Edition)*.  Upper Saddle River, NJ, USA: Prentice-Hall,  2006.
2. S. M. Pizer, E. P. Amburn, J. D. Austin, R. Cromartie, A. Geselowitz, T. Greer, B. ter Haar Romeny, J. B. Zimmerman and K. Zuiderveld “Adaptive histogram equalization and its variations,” *Computer Vision, Graphics, and Image Processing*, vol. 38, no. 1, p. 99, Apr. 1987. [10.1016/S0734-189X(87)80186-X](https://doi.org/10.1016/s0734-189x(87)80156-1)
3. W. H. Press, S. A. Teukolsky, W. T. Vetterling, and B. P. Flannery.  *Numerical Recipes: The Art of Scientific Computing (3rd Edition)*. New York, NY, USA: Cambridge University Press, 2007.

See also: [histmatch](@ref),[histeq](@ref), [imhist](@ref) and  [adjust_gamma](@ref).
