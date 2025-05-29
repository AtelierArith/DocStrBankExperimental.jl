```
LinearBSpline(path::String)
```

A function that reads in the `x` and `y` values for [`LinearBSpline`](@ref) from a .txt file. The input values are:

  * `path`: String of a path of the specific .txt file

The .txt file has to have the following structure to be interpreted by this function:

  * First line: comment `# Number of x values`
  * Second line: integer which gives the number of `x` values
  * Third line: comment `# x values`
  * Following lines: the `x` values where each value has its own line
  * Line after the x-values: comment `# y values`
  * Remaining lines: `y` values where each value has its own line

Note that the number of `x` and `y` values have to be the same. An example can be found [here](https://gist.githubusercontent.com/maxbertrand1996/b05a90e66025ee1ebddf444a32c3fa01/raw/90d375c1ac11b26589aab1fe92bd0e6f6daf37b7/Rhine_data_1D_10.txt)
