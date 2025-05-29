```
err_pd(Ie)
```

Calculate the error (up to permuataion and rescaling) between Ie and identity matrix:

$$
err = \mathrm{min}_{P, D} ||PDI_{e} - I||_{F},
$$

where $P$ runs over all permuataion matrices and $D$ runs over all diagonal non-singular matrices. $||~||_F$ denotes the Frobeneous norm. 

# Arguments

  * `Ie`: the input matrix, supposed to be close to identity matrix.

# Outputs

  * `err`: the error between `Ie` and identity matrix defined as above.
