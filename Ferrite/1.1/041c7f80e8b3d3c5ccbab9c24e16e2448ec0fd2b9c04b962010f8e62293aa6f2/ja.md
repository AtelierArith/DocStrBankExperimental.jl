```
function_gradient(fe_v::AbstractValues{dim}, q_point::Int, u::AbstractVector, [dof_range])
```

四分点での関数の勾配を計算します。`u`は自由度の値を持つベクトルです。スカラー値の関数の場合、`u`はスカラーを含みます。ベクトル値の関数の場合、`u`はスカラーのベクトル（`VectorValues`を使用するため）または`u`は`Vec`のベクトル（`ScalarValues`と一緒に使用するため）であることができます。

スカラー関数または`VectorValues`を使用したベクトル値関数の勾配は、$\mathbf{\nabla} u(\mathbf{x}) = \sum\limits_{i = 1}^n \mathbf{\nabla} N_i (\mathbf{x}) u_i$または$\mathbf{\nabla} u(\mathbf{x}) = \sum\limits_{i = 1}^n \mathbf{\nabla} \mathbf{N}_i (\mathbf{x}) u_i$として計算されます。ここで、$u_i$は関数のノード値です。`ScalarValues`を使用したベクトル値関数の勾配は、$\mathbf{\nabla} \mathbf{u}(\mathbf{x}) = \sum\limits_{i = 1}^n \mathbf{u}_i \otimes \mathbf{\nabla} N_i (\mathbf{x})$として計算され、ここで$\mathbf{u}_i$は$\mathbf{u}$のノード値です。
