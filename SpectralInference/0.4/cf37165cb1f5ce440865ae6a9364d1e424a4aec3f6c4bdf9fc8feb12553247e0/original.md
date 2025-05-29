```
squareform(d::AbstractVector, fillvalue=zero(eltype(d)))
squareform(d::AbstractVector, fillvalue=zero(eltype(d)))
```

If `d` is a vector, `squareform` checks if it of `n` choose 2 length for integer `n`, then fills the values of a symetric square matrix with the values of `d`.

If `d` is a matrix, `squareform` checks if it is square then fills the values of vector with the lower offdiagonal of matrix `d` in column order form. 

`fillvalue` is the initial value of the produced vector or matrix. Only really apparant in a produced matrix where it will be the values on the diagonal.
