```
project(t::Tensor{dim},bases_tensor::Tuple{Vararg{BaseTensor{dim,1},dim}}=(e₁,e₂,e₃)) where dim
```

Project `t` to a tensor with the base tensor `bases` and return it. This function can also be used to simplfy `t`'s base tensors to be independent.
