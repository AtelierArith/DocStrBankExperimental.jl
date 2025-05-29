```
create_tabulation_1D(
    func::Function[,
    args...];
    xmin::T,
    xmax::T,
    npoints::Int[,
    x_scale::Symbol = :linear,
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
) where {T<:Union{Real,Quantity}}
```

与えられた関数 `f(x)` のタブレーションを計算またはロードします。

# 引数

  * `func::Function`: タブレーションすべき関数。`f(x)` の形式である必要があります。
  * `xmin::Union{Real,Quantity}`: タブレーションでカバーされる範囲の最小 `x`
  * `xmax::Union{Real,Quantity}`: タブレーションでカバーされる範囲の最大 `x`
  * `npoints::Int`: `f(x)` が計算されるポイントの数
  * `x_scale::Symbol`: タブレーションに使用されるスケール。`:linear` が選択されると、`x` ポイントは均等に間隔を置かれます。`:log10` が選択されると、ポイントは対数的に間隔を置かれます。デフォルトは `:linear`
  * `f_scale::Symbol`: タブレーションに使用されるスケール。`:linear` が選択されると、`f(x)` ポイントは変更されません。`:log10` が選択されると、補間の前に `f(x)` ポイントに log10 が適用されます。デフォルトは `:linear`
  * `jld_base_path::String`: タブレーションが保存されるフォルダーへのパス。デフォルトは現在のフォルダー
  * `custom_name::String`: タブレーションファイルのカスタム名。`_data.jld2` が追加されます。デフォルトはタブレーションされる関数の名前
  * `interpolation_type::Symbol`: 補間に使用されるスプラインのタイプ。`:linear`（1次スプライン）または `:cubic`（3次スプライン）のいずれか
  * `extrapolation_bc`: `[xmin, xmax]` で定義された境界の外側でのタブレーションの動作。可能な動作は Interpolations.jl によって処理され、`Throw`（境界外の値にアクセスするとエラーをスロー）または `Line`（線形に外挿）を含みます。デフォルトは `Throw`
  * `check_SHA::Bool`: タブレーションされた関数のSHAをチェックするかどうか。タブレーションされた関数のSHAがタブレーションファイル内に保存されたSHAと一致しない場合、タブレーションを再計算する必要があるかもしれません。これは、タブレーションされた関数の定義が変更された可能性が高いためです。
  * `check_SHA_mode::Symbol`: タブレーションされた関数のSHAがタブレーションファイル内に保存されたSHAと一致しない場合のこの関数の動作を説明します。デフォルトは `:warn`（警告を表示しますが、タブレーションを同様にロードします）。他のオプションには `:throw`（古いタブレーションの手動削除を提案するエラーをスロー）や `:none`（何もしない）が含まれます。
  * `metadata::Dict{String,Any}`: タブレーションアーカイブに保存される追加のメタデータを含むオプションの `Dict{String, Any}`。
  * `metadata_validation_fn::Function`: 2つのメタデータ辞書が同じデータを含むかどうかを確認するための `metadata_validation_fn(metadata1::Dict{String, Any}, metadata2::Dict{String, Any})` の形式の関数。
  * `args..., kwargs...`: タブレーションされる関数に渡される追加の `args` と `kwargs`

# 例

```jldoctest
julia>  func_1d(x) = sin(x)

julia>  itp_1d_1 = create_tabulation_1D(
            func_1d,
            xmin = 0.0,
            xmax = 3.0,
            npoints = 100,
            x_scale = :linear,
            f_scale = :linear
        )

julia>  isapprox(itp_1d_1(2.0), func_1d(2.0), rtol = 1e-3)
true
```

測定単位もサポートされています：

```jldoctest
julia>  using Unitful

julia>  func_1d(x) = x^2

julia>  itp_1d_1 = create_tabulation_1D(
            func_1d,
            xmin = 0.0u"m",
            xmax = 3.0u"m",
            npoints = 100,
            x_scale = :linear,
            f_scale = :linear
        )

julia>  isapprox(itp_1d_1(2.0u"m"), func_1d(2.0u"m"), rtol = 1e-3)
true
```
