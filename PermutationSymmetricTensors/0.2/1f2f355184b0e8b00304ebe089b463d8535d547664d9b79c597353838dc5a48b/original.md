function find*symmetric*tensor_size(N, dim)

```
Returns the number of elements of a symmetric tensor of dimension dim of N elements in each dimension. 
The results is given by binomial(N-1+dim, dim).

Example:
julia> find_symmetric_tensor_size(20, 6)
177100
```
