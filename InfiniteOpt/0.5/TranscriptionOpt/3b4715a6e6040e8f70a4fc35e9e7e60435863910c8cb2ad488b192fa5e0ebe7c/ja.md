```
TranscriptionData
```

[`InfiniteOpt.InfiniteModel`](@ref) から通常の `JuMP.Model` に転写されたデータを格納するためのデータ型で、転写された変数を含みます。これは `JuMP.Model` の `ext` フィールドに格納され、[`TranscriptionModel`](@ref) コンストラクタを介して `TranscriptionModel` と呼ばれるものを作成します。

**フィールド**

  * `infvar_lookup::Dict{InfiniteOpt.GeneralVariableRef, Dict{Vector{Float64}, Int}}`:  サポート値を介した無限変数の転写のルックアップテーブル。
  * `infvar_mappings::Dict{InfiniteOpt.GeneralVariableRef, Vector{JuMP.VariableRef}}`:  無限変数をその転写変数にマッピングします。
  * `infvar_supports::Dict{InfiniteOpt.GeneralVariableRef, Vector{Tuple}}`:  無限変数をそのサポート値にマッピングします。
  * `infvar_support_labels::Dict{InfiniteOpt.GeneralVariableRef, Vector{Set{DataType}}}`:   無限変数をそのサポートラベルにマッピングします。
  * `finvar_mappings::Dict{InfiniteOpt.GeneralVariableRef, JuMP.VariableRef}`:  有限変数をその転写変数にマッピングします。
  * `semi_infinite_vars::Vector{InfiniteOpt.SemiInfiniteVariable{InfiniteOpt.GeneralVariableRef}}`:  転写に基づいて形成された半無限変数のコアオブジェクトを格納します。
  * `semi_lookup::Dict{Tuple{InfiniteOpt.GeneralVariableRef, Dict{Int, Float64}}, InfiniteOpt.GeneralVariableRef}`:  すでに追加された半無限変数をルックアップします。
  * `last_point_index::Int`: 追加された最後の内部点変数インデックス。
  * `point_lookup::Dict{Tuple{InfiniteOpt.GeneralVariableRef, Vector{Float64}}, InfiniteOpt.GeneralVariableRef}`:  すでに内部で作成された点変数をルックアップします。
  * `measure_lookup::Dict{InfiniteOpt.GeneralVariableRef, Dict{Vector{Float64}, Int}}`:  サポート値を介した測定の転写のルックアップテーブル。
  * `measure_mappings::Dict{InfiniteOpt.GeneralVariableRef, Vector{JuMP.AbstractJuMPScalar}}`:  測定を転写式にマッピングします。
  * `measure_supports::Dict{InfiniteOpt.GeneralVariableRef, Vector{Tuple}}`:  測定をそのサポート値にマッピングします（転写された測定がまだ無限の場合）。
  * `measure_support_labels::Dict{InfiniteOpt.GeneralVariableRef, Vector{Set{DataType}}}`:   測定をそのサポートラベルにマッピングします（もしあれば）。
  * `constr_mappings::Dict{InfiniteOpt.InfOptConstraintRef, Vector{JuMP.ConstraintRef}}`:  制約をその転写にマッピングします。
  * `constr_supports::Dict{InfiniteOpt.InfOptConstraintRef, Vector{Tuple}}`:  制約をそのサポート値にマッピングします。
  * `constr_support_labels::Dict{InfiniteOpt.InfOptConstraintRef, Vector{Set{DataType}}}`:   制約をそのサポートラベルにマッピングします。
  * `supports::Tuple`:  収集されたパラメータサポートをここに格納します。
  * `support_labels::Tuple`:  収集されたパラメータラベルをここに格納します。
  * `has_internal_supports::Bool`:  収集された内部サポートはありますか？
