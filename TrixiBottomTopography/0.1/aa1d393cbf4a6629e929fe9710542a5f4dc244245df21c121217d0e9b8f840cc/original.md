```
BilinearBSpline(path::String)
```

A function which reads in the `x`, `y` and `z` values for [`BilinearBSpline`](@ref) from a .txt file. The input values are:

  * `path`: String of a path of the specific .txt file

The .txt file has to have the following structure to be interpreted by this function:

  * First line: comment `# Number of x values`
  * Second line: integer which gives the number of `x` values
  * Third line: comment `# Number of y values`
  * Fourth line: integer which gives the number of `y` values
  * Fifth line: comment `# x values`
  * Following lines: the `x` values where each value has its own line
  * Line after the x-values: comment `# y values`
  * Following lines: `y` values where each value has its own line
  * Line after the y-values: comment `# z values`
  * Remaining lines: values for `z` where each value has its own line and is in the following order:                  z*11, z*12, ... z*1n, z*21, ... z*2n, ..., z*m1, ..., z_mn

An example can be found [here](https://gist.githubusercontent.com/maxbertrand1996/7b1b943eac142d5bc836bb818fe83a5a/raw/74228e349e91fbfe1563479f99943b469f26ac62/Rhine_data_2D_10.txt)
