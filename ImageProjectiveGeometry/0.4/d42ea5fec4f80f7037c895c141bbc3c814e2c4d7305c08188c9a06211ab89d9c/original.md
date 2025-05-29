briefcoords - Compute BRIEF descriptor sampling coordinates within a patch.

```
Usage:  rc = briefcoords(S, nPairs, UorG; disp=false)

Arguments:  S - An odd integer specifying the patch size (S x S).
       nPairs - Number of point pairs required.  Typically this is a power
                of 2, 128, 256, 512 for packing the descriptor values into
                a bit string.
         UorG - Character 'U' or 'G' indicating whether a uniform or
                gaussian distribution of point pairings is formed within
                the patch.
         disp - Optional boolean flag indicating whether a plot of the point
                pairings should be displayed.

Returns:   rc - [2 x 2*nPairs] array of integer (row; col) coordinates
                with all values in the range -(S-1)/2..(S-1)/2.  Each
                successive pair of columns is intended to provide a pair of
                points for comparing image grey values against each other
                for forming a BRIEF descriptor of a patch about some
                central feature location.
```

Use of the Gaussian distribution of point pairings corresponds to the approach suggested by Calonder et al in their original paper.  Note, however that for small patches and a large number of pairings one will get repeated pairings which reduces the degrees of freedom in the final descriptor.  The uniformly distributed option does not result in repeated pairings making it the preferred option for small patch sizes.

See also: grey2lbp(), grey2lbp!()
