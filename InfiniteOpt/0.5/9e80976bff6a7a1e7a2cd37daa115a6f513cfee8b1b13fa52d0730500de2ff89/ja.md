```
GeneralVariableRef <: JuMP.AbstractVariableRef
```

`InfiniteOpt`における変数式を構築するための主要な変数参照として機能する`DataType`です。これは、`index_type`に基づいて[`DispatchVariableRef`](@ref)の正しいサブタイプを取得するために、[`dispatch_variable_ref`](@ref)を介して変数タイプ特有の参照（例：[`InfiniteVariableRef`](@ref)）を作成するために必要な情報を含んでいます。これにより、以前の`InfiniteOpt`バージョンとは異なり、具体的なコンテナを使用して式を構築できるため、パフォーマンスが大幅に向上します。

**フィールド**

  * `model::InfiniteModel`: 無限モデル。
  * `raw_index::Int64`: `index_type`コンストラクタで使用される生のインデックス。
  * `index_type::DataType`: 具体的な[`AbstractInfOptIndex`](@ref)タイプ/コンストラクタ。
  * `param_index::Int`: [`DependentParameters`](@ref)内のパラメータのインデックス。これは他の変数タイプには無視されます。
