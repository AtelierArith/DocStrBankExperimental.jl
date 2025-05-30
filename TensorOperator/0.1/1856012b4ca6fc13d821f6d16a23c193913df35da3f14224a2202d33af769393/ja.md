```
project(t::Tensor{dim},bases_tensor::Tuple{Vararg{BaseTensor{dim,1},dim}}=(e₁,e₂,e₃)) where dim
```

`t`を基底テンソル`bases`を持つテンソルに射影し、それを返します。この関数は、`t`の基底テンソルを独立に簡略化するためにも使用できます。
