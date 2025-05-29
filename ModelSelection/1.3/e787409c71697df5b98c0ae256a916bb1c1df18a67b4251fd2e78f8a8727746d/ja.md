生データを適切なデータ型に変換します。

# パラメータ

  * `datatype::Type`: データ型。
  * `depvar_data::Union{Vector{Float32}, Vector{Float64}, Vector{Union{Float32, Missing}}, Vector{Union{Float64, Missing}}}`: 従属変数データ。
  * `expvars_data::Union{Array{Float32}, Array{Float64}, Array{Union{Float32, Missing}}, Array{Union{Float64, Missing}}}`: 説明変数データ。
  * `fixedvariables::Union{Array{Float32}, Array{Float64}, Array{Union{Float32, Missing}}, Array{Union{Float64, Missing}}, Nothing}`: 固定変数データ。
  * `time_data::Union{Array{Float32}, Array{Float64}, Array{Union{Float32, Missing}}, Array{Union{Float64, Missing}}, Nothing}`: 時間変数データ。
  * `panel_data::Union{Array{Float32}, Array{Float64}, Array{Union{Float32, Missing}}, Array{Union{Float64, Missing}}, Nothing}`: パネル変数データ。
