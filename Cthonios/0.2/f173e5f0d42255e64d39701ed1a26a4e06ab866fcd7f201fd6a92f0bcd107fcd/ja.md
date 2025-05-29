```julia
struct DirichletBC{N, D, F} <: Cthonios.AbstractBCInput
```

  * `nset_name::Any`
  * `dofs::Any`
  * `func::Any`

スクリプトまたは入力ファイルからの入力に使用される基本的なディリクレ境界条件タイプ。 `nset_name`はエクソダスファイル内のノードセットの名前に対応し、`dofs`はこの境界条件が適用されるインデックス付きフィールドに対応し、`func`はフィールドに適用する関数です。
