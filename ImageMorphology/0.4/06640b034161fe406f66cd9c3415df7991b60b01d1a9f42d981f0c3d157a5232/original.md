Max-tree morphological representation of an image.

# Details

Let's consider a *thresholding* operation,

```julia
    mask = [val ≥ threshold for val in image]
```

One can identify the connected components (the sets of neighboring true values) in `mask`. When *image thresholding* is sequentially applied for all possible thresholds, it generates a collection of connected components that could be organized into a hierarchical structure called *component tree*. Consider 1D "image" with values 1, 2 and 3:

```
       2233233312223322
```

The connected components would be

```
    1: AAAAAAAAAAAAAAAA
    2: BBBBBBBB.CCCCCCC
    3: ..DD.EEE....FF..
```

Here, the letters are the labels of the resulting connected components, and `.` specifies that the pixel value is below the threshold. In this example, the corresponding *component tree* is:

```
      A
     ⭩ ⭨
    B   C
   ⭩ ⭨   ⭨
  D   E   F
```

A *max-tree* is an efficient representation of the *component tree*. A connected component $C$ at threshold level $t$ is represented by the single *reference pixel* $r$ from this level (`image[r] == t`), which is the parent to all other pixels of $C$ and also to the *reference pixels* of the connected components at higher thresholds, which are the children of $C$. In our example, the reference pixels (denoted by the letter of the corresponding component) would be:

```
    1: ........A.......
    2: B........C......
    3: ..D..E......F...
```

I.e.

| Comp | Ref.Pixel |
| ----:| ---------:|
|  *A* |         9 |
|  *B* |         1 |
|  *C* |        10 |
|  *D* |         3 |
|  *E* |         6 |
|  *F* |        13 |

So the whole max-tree could be encoded as a vector of indices of parent pixels:

```
9  1  1  3  1  1  6  6  9  9 10 10 10 13 10 10
```

The *max-tree* is the basis for many morphological operators, namely connected operators. Unlike morphological openings and closings, these operators do not require a fixed structuring element, but rather act with a flexible structuring element that meets a certain criterion.

# See also

[`area_opening`](@ref), [`area_closing`](@ref), [`diameter_opening`](@ref), [`diameter_closing`](@ref).

# References

1. Salembier, P., Oliveras, A., & Garrido, L. (1998). *Antiextensive Connected Operators for Image and Sequence Processing*. IEEE Transactions on Image Processing, 7(4), 555-570.

    > https://doi.org/10.1109/83.663500
2. Berger, C., Geraud, T., Levillain, R., Widynski, N., Baillard, A., Bertin, E. (2007). *Effective Component Tree Computation with Application to Pattern Recognition in Astronomical Imaging*. In International Conference on Image Processing (ICIP), 41-44.

    > https://doi.org/10.1109/ICIP.2007.4379949
3. Najman, L., & Couprie, M. (2006). *Building the component tree in quasi-linear time*. IEEE Transactions on Image Processing, 15(11), 3531-3539.

    > https://doi.org/10.1109/TIP.2006.877518
4. Carlinet, E., & Geraud, T. (2014). *A Comparative Review of Component Tree Computation Algorithms*. IEEE Transactions on Image Processing, 23(9), 3885-3895.

    > https://doi.org/10.1109/TIP.2014.2336551
