```
n_product_id( tensor_coord :: Vector{Int64}, dims :: Vector{Int64} ) :: Int64
```

For a given tensor product of subspace dimension `dims` and tensor coordingate `tensor_coord` returns the corresponding matrix index of the kronecker product. The tenosr product `dims` is a vector of positive definite integers specifying the dimension of each of the matrices in the tensor product. The `tensor_coord` is a vector of positive definite integers specifying the target index in each matrix in the tensor product. The `dims` and `tensor_coord` should describe either row or column indices of the tensor product.

A `DomainError` is thrown if any index in `tensor_coord` is not valid or the number of elements in `tensor_coord` does not equal that of `dims`.
