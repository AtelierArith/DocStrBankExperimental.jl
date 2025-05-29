```
mri_read_bfiles!(dwi::MRI, infile1::String, infile2::String)
```

Set the .bval and .bvec fields of the MRI structure `dwi`, by reading a DWI b-value table and gradient table from the text files `infile1` and `infile2`. The two input files can be specified in any order. The gradient table file must contain 3 times as many entries as the b-value table file.

Return the b-value table as a vector of size n and the gradient table as a matrix of size (n, 3).
