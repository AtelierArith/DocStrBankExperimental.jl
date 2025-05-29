```
function_value(fe_v::AbstractValues, q_point::Int, u::AbstractVector, [dof_range])
```

四分点での関数の値を計算します。`u`は自由度の値を持つベクトルです。スカラー値関数の場合、`u`はスカラーを含みます。ベクトル値関数の場合、`u`はスカラーのベクトル（`VectorValues`を使用するため）または`u`は`Vec`のベクトル（ScalarValuesと一緒に使用するため）であることができます。

スカラー値関数の値は$u(\mathbf{x}) = \sum\limits_{i = 1}^n N_i (\mathbf{x}) u_i$として計算され、ここで$u_i$はノードにおける$u$の値です。ベクトル値関数の場合、値は$\mathbf{u}(\mathbf{x}) = \sum\limits_{i = 1}^n N_i (\mathbf{x}) \mathbf{u}_i$として計算され、ここで$\mathbf{u}_i$は$\mathbf{u}$のノード値です。 ```
