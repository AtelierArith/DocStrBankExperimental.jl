```
create_tabulation_3D(
    func::Function[,
    args...];
    xmin::T,
    xmax::T,
    ymin::V,
    ymax::V,
    zmin::W,
    zmax::W,
    npoints_x::Int,
    npoints_y::Int,
    npoints_z::Int[,
    x_scale::Symbol = :linear,
    y_scale::Symbol = :linear,
    z_scale::Symbol = :linear,
    f_scale = :linear,
    jld_base_path = nothing,
    custom_name = nothing,
    interpolation_type = :linear,
    extrapolation_bc = Throw,
    check_SHA = true,
    check_SHA_mode = :warn,
    metadata=nothing,
    metadata_validation_fn=nothing,
    kwargs...]
) where {T<:Union{Real,Quantity},V<:Union{Real,Quantity},W<:Union{Real,Quantity}}
```

与えられた関数 `f(x, y, z)` のタブレーションを計算またはロードします。

# 引数

  * `func::Function`: タブレーションすべき関数。`f(x, y)` の形式である必要があります。
  * `xmin::Union{Real,Quantity}`: タブレーションでカバーされる範囲の最小 `x`
  * `xmax::Union{Real,Quantity}`: タブレーションでカバーされる範囲の最大 `x`
  * `ymin::Union{Real,Quantity}`: タブレーションでカバーされる範囲の最小 `y`
  * `ymax::Union{Real,Quantity}`: タブレーションでカバーされる範囲の最大 `y`
  * `zmin::Union{Real,Quantity}`: タブレーションでカバーされる範囲の最小 `z`
  * `zmax::Union{Real,Quantity}`: タブレーションでカバーされる範囲の最大 `z`
  * `npoints_x::Int`: `f(x,y,z)` が計算される `x` 軸に沿ったポイントの数
  * `npoints_y::Int`: `f(x,y,z)` が計算される `y` 軸に沿ったポイントの数
  * `npoints_z::Int`: `f(x,y,z)` が計算される `z` 軸に沿ったポイントの数
  * `x_scale::Symbol`: タブレーションに使用されるスケール。`:linear` が選択された場合、`x` ポイントは均等に配置されます。`:log10` が選択された場合、ポイントは対数的に配置されます。デフォルトは `:linear`
  * `y_scale::Symbol`: タブレーションに使用されるスケール。`:linear` が選択された場合、`y` ポイントは均等に配置されます。`:log10` が選択された場合、ポイントは対数的に配置されます。デフォルトは `:linear`
  * `z_scale::Symbol`: タブレーションに使用されるスケール。`:linear` が選択された場合、`z` ポイントは均等に配置されます。`:log10` が選択された場合、ポイントは対数的に配置されます。デフォルトは `:linear`
  * `f_scale::Symbol`: タブレーションに使用されるスケール。`:linear` が選択された場合、`f(x)` ポイントは変更されません。`:log10` が選択された場合、補間前に `f(x)` ポイントに log10 が適用されます。デフォルトは `:linear`
  * `jld_base_path`: タブレーションが保存されるフォルダーへのパス。デフォルトは現在のフォルダー
  * `custom_name`: タブレーションファイルのカスタム名。`_data.jld2` が追加されます。デフォルトはタブレーションされる関数の名前
  * `interpolation_type`: 補間に使用されるスプラインのタイプ。`:linear`（1次スプライン）または `:cubic`（3次スプライン）のいずれか
  * `extrapolation_bc`: `[xmin, xmax]` で定義された境界の外側でのタブレーションの動作。可能な動作は Interpolations.jl によって処理され、`Throw`（範囲外の値にアクセスするとエラーを投げる）または `Line`（線形に外挿する）が含まれます。デフォルトは `Throw`
  * `check_SHA::Bool`: タブレーションされた関数のSHAをチェックするかどうか。タブレーションされた関数のSHAがタブレーションファイル内に保存されたSHAと一致しない場合、タブレーションを再計算する必要があるかもしれません。これは、タブレーションされた関数の定義が変更された可能性が高いためです。
  * `check_SHA_mode::Symbol`: タブレーションされた関数のSHAがタブレーションファイル内に保存されたSHAと一致しない場合のこの関数の動作を説明します。デフォルトは `:warn`（警告を表示しますが、タブレーションを同様にロードします）。他のオプションには `:throw`（古いタブレーションの手動削除を提案するエラーを投げる）と `:none`（何もしない）が含まれます。
  * `metadata::Dict{String,Any}`: タブレーションアーカイブに保存される追加のメタデータを含むオプションの `Dict{String, Any}`。
  * `metadata_validation_fn::Function`: 2つのメタデータ辞書が同じデータを含むかどうかをチェックするための `metadata_validation_fn(metadata1::Dict{String, Any}, metadata2::Dict{String, Any})` の形式の関数。
  * `args..., kwargs...`: 追加の `args` と `kwargs` は、タブレーションされる関数に渡されます。

# 例

```jldoctest
julia>  func_3d(x, y, z) = x * y + z

julia>  itp_3d_1 = create_tabulation_3D(
            func_3d,
            xmin = 0.0,
            xmax = 1.0,
            ymin = 0.0,
            ymax = 2.0,
            zmin = 0.0,
            zmax = 3.0,
            npoints_x = 100,
            npoints_y = 100,
            npoints_z = 100,
        )

julia>  isapprox(itp_3d_1(1.0, 1.3, 2.5), func_3d(1.0, 1.3, 2.5), rtol = 1e-3)
true
```

測定単位もサポートされています：

```jldoctest
julia>  using Unitful

julia>  func_3d(x, y, z) = x * y + z

julia>  itp_3d_1 = create_tabulation_3D(
            func_3d,
            xmin = 0.0u"m",
            xmax = 1.0u"m",
            ymin = 0.0"s^-1",
            ymax = 2.0"s^-1",
            zmin = 0.0u"m/s",
            zmax = 3.0u"m/s",
            npoints_x = 100,
            npoints_y = 100,
            npoints_z = 100,
        )

julia>  isapprox(itp_3d_1(1.0u"m", 1.3u"s^-1", 2.5u"m/s"), func_3d(1.0u"m", 1.3u"s^-1", 2.5u"m/s"), rtol = 1e-3)
true
```
