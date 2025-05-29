```
function_value(iv::InterfaceValues, q_point::Int, u; here::Bool)
function_value(iv::InterfaceValues, q_point::Int, u, dof_range_here, dof_range_there; here::Bool)
```

インターフェースの「ここ」(`here=true`)または「そこ」(`here=false`)側の四分点 `q_point` で関数の値を計算します。`u_here` と `u_there` はそれぞれの要素の自由度の値です。

`u` は自由度のスカラー値のベクトルです。この関数は、インターフェースの両方の要素の自由度を含む単一の `u` ベクトルまたは、それぞれのセルの自由度を含む二つのベクトル（`u_here` と `u_there`）で使用できます。

`here` は関数値を計算するために使用する要素を決定します。`true` はインターフェースの最初の要素の側の値を使用し、`false` は二番目の要素の側の値を使用します。

スカラー値関数の値は $u(\mathbf{x}) = \sum\limits_{i = 1}^n N_i (\mathbf{x}) u_i$ として計算され、ここで $u_i$ はノードにおける $u$ の値です。ベクトル値関数の値は $\mathbf{u}(\mathbf{x}) = \sum\limits_{i = 1}^n N_i (\mathbf{x}) \mathbf{u}_i$ として計算され、ここで $\mathbf{u}_i$ は $\mathbf{u}$ のノード値です。
