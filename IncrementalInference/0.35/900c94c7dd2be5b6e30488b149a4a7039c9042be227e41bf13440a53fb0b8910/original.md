```julia
localProduct(dfg, sym; solveKey, N, dbg, logger)

```

Using factor graph object `dfg`, project belief through connected factors (convolution with likelihood) to variable `sym` followed by a approximate functional product.

Return: product belief, full proposals, partial dimension proposals, labels
