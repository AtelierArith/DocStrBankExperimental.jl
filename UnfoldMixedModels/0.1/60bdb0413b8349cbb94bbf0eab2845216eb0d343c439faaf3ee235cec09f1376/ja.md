fit!(uf::UnfoldModel,data::Union{<:AbstractArray{T,2},<:AbstractArray{T,3}}) where {T<:Union{Missing, <:Number}}

2D/3D配列データに対してDesignMatrixをフィットします。データは通常、チャネル x 時間（基底関数を使用）またはチャネル x 時間 x エポック（マスユニバリアント用）として解釈されます。

  * `show_progress`（デフォルト:true）、プログレスメーターを無効にします。

UnfoldModelオブジェクトを返します。

# 例

```julia-repl

```
