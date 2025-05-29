```
split_and_flatten(input::AbstractArray)::AbstractArray
```

Perform a preprocessing of an image into *flattened patches*.

This rearranges the input data so that it can easily be processed with a transformer.

# Examples

Consider a matrix of size $6\times6$ which we want to divide into patches of size $3\times3$.

```jldoctest
using GeometricMachineLearning

input = [ 1  2  3  4  5  6; 
          7  8  9 10 11 12; 
         13 14 15 16 17 18;
         19 20 21 22 23 24; 
         25 26 27 28 29 30; 
         31 32 33 34 35 36]

split_and_flatten(input; patch_length = 3, number_of_patches = 4)

# output

9×4 Matrix{Int64}:
  1  19   4  22
  7  25  10  28
 13  31  16  34
  2  20   5  23
  8  26  11  29
 14  32  17  35
  3  21   6  24
  9  27  12  30
 15  33  18  36
```

Here we see that `split_and_flatten`:

1. *splits* the original matrix into four $3\times3$ matrices and then
2. *flattens* each matrix into a column vector of size $9.$

After this all the vectors are put together again to yield a $9\times4$ matrix.

# Arguments

The optional keyword arguments are: 

  * `patch_length`: by default this is 7.
  * `number_of_patches`: by default this is 16.

The sizes of the first and second axis of the output of `split_and_flatten` are 

1. $\mathtt{path\_length}^2$ and
2. `number_of_patches`.
