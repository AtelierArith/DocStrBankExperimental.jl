```
BdryGpBasisFns(line_gp_fns::LineGpBasisFns, perp_edge_fns::GpBasisFnsζ, bdry::Boundary)
```

境界上のすべてのガウス点での2次元Bスプライン基底関数とその導関数。

[`LineGpBasisFns`](@ref)構造体`line_gp_fns`は、各要素に対して`ngp`のガウス点を持つ境界に沿ったすべての1次元基底関数とその導関数を含みます。ここで、`perp_edge_fns`は、[`GpBasisFnsζ`](@ref)構造体に含まれる直交パラメトリック方向での境界における基底関数とその導関数です。例えば、`RIGHT`境界では、`line_gp_fns`は$ζ^2$方向の1次元導関数をキャプチャし、`perp_edge_fns`は右端での$ζ^1$方向の1次元導関数を含みます。基礎となるテンソル積構造[piegl-tiller](@citep)の知識を用いて、指定された[`Boundary`](@ref) `bdry`に沿った2次元基底関数が生成されます。この構造体には4つのフィールドがあります：

  * `nel` –> [`LineGpBasisFns`](@ref) `line_gp_fns`に関連する要素の数
  * `uel_ids` –> `elem_id`から`unique_elem_id`へのマッピング
  * `ufns` –> 型[`GpBasisFnsζα`](@ref)のユニークな2次元基底関数の`num_unique_elems`×`ngp`行列
  * `bdry` –> パラメトリックドメインの[`Boundary`](@ref)

```
