```
FacetValues([::Type{T}], quad_rule::FacetQuadratureRule, func_interpol::Interpolation, [geom_interpol::Interpolation])
```

`FacetValues`オブジェクトは、有限要素のファセット上での形状関数の値、形状関数の勾配、ノード関数の値、ノード関数の勾配および発散などの評価プロセスを容易にします。

**引数:**

  * `T`: 内部データが格納される型を決定するオプション引数（デフォルトは`Float64`）。
  * `quad_rule`: [`FacetQuadratureRule`](@ref)のインスタンス
  * `func_interpol`: 近似関数を補間するために使用される[`Interpolation`](@ref)のインスタンス
  * `geom_interpol`: 幾何学を補間するために使用されるオプションの[`Interpolation`](@ref)のインスタンス。デフォルトでは線形ラグランジュ補間が使用されます。

**キーワード引数:** 次のキーワード引数は実験的であり、将来のマイナーリリースで変更される可能性があります。

  * `update_gradients`: 形状関数の勾配を更新するかどうかを指定します（デフォルトはtrue）。
  * `update_hessians`: 形状関数のヘッセ行列を更新するかどうかを指定します（デフォルトはfalse）。

**一般的なメソッド:**

  * [`reinit!`](@ref)
  * [`getnquadpoints`](@ref)
  * [`getdetJdV`](@ref)
  * [`shape_value`](@ref)
  * [`shape_gradient`](@ref)
  * [`shape_symmetric_gradient`](@ref)
  * [`shape_divergence`](@ref)
  * [`function_value`](@ref)
  * [`function_gradient`](@ref)
  * [`function_symmetric_gradient`](@ref)
  * [`function_divergence`](@ref)
  * [`spatial_coordinate`](@ref)

```
