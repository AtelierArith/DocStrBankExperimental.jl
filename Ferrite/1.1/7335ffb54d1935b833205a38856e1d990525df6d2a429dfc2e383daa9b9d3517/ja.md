```
function_gradient(iv::InterfaceValues, q_point::Int, u; here::Bool)
function_gradient(iv::InterfaceValues, q_point::Int, u, dof_range_here, dof_range_there; here::Bool)
```

四分点での関数の勾配を計算します。`u`は自由度のスカラー値のベクトルです。この関数は、インターフェースの両方の要素の自由度を含む単一の`u`ベクトルまたは、それぞれのセルの自由度を含む2つのベクトル（`u_here`と`u_there`）で使用できます。

`here`は、関数値を計算するために使用する要素を決定します。`true`はインターフェースの最初の要素の側の値を使用し、`false`は2番目の要素の側の値を使用します。

スカラー関数または`VectorValues`を使用したベクトル値関数の勾配は、$\mathbf{\nabla} u(\mathbf{x}) = \sum\limits_{i = 1}^n \mathbf{\nabla} N_i (\mathbf{x}) u_i$または$\mathbf{\nabla} u(\mathbf{x}) = \sum\limits_{i = 1}^n \mathbf{\nabla} \mathbf{N}_i (\mathbf{x}) u_i$として計算されます。ここで、$u_i$は関数のノード値です。`ScalarValues`を使用したベクトル値関数の勾配は、$\mathbf{\nabla} \mathbf{u}(\mathbf{x}) = \sum\limits_{i = 1}^n \mathbf{u}_i \otimes \mathbf{\nabla} N_i (\mathbf{x})$として計算され、ここで$\mathbf{u}_i$は$\mathbf{u}$のノード値です。
