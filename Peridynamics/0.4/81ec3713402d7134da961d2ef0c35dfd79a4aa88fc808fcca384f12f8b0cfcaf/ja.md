```
Body(material, position, volume)
Body(material, inp_file)
```

パラダイナミクスシミュレーションのための `Body` を構築します。

# 引数

  * `material::AbstractMaterial`: ボディ全体に定義された材料。 利用可能な材料モデル：

      * [`BBMaterial`](@ref): ボンドベースのパラダイナミクス
      * [`OSBMaterial`](@ref): 通常の状態ベースのパラダイナミクス
      * [`CMaterial`](@ref): 対応形式
      * [`BACMaterial`](@ref): Chen と Spencer のボンド関連対応形式
      * [`CKIMaterial`](@ref): 連続体運動学にインスパイアされたパラダイナミクス
  * `position::AbstractMatrix`: `n` 点の位置を持つ `3×n` 行列。
  * `volume::AbstractVector`: 各点の体積を持つベクトル。
  * `inp_file::AbstractString`: メッシュを含む Abaqus 入力ファイルで、[`read_inp`](@ref) でインポートされます。

# 例外

  * 点の数がゼロより大きくない場合はエラー。
  * `position` が `3×n` 行列でなく、`volume` と同じ長さでない場合はエラー。
  * `position` または `volume` に `NaN` 値が含まれている場合はエラー。

# 例

```julia-repl
julia> Body(BBMaterial(), rand(3, 10), rand(10))
10-point Body{BBMaterial{NoCorrection}}:
  1 point set(s):
    10-point set `all_points`
```

---

!!! 警告 "内部使用のみ"     フィールドは内部使用のみを目的としていることに注意してください。これらは Peridynamics.jl の公開 API の一部ではなく、したがって、破壊的変更と見なされることなく、いつでも変更（または削除）される可能性があります。

```julia
Body{Material,PointParameters}
```

# 型パラメータ

  * `Material <: AbstractMaterial`: 指定された材料モデルの型。
  * `PointParameters <: AbstractPointParameters`: 点パラメータの型。

# フィールド

  * `mat::Material`: 材料の定式化。
  * `n_points::Int`: ボディ内の点の数。
  * `position::Matrix{Float64}`: 点の位置を持つ `3×n_points` 行列。
  * `volume::Vector{Float64}`: 各点の体積を持つベクトル。
  * `fail_permit::Vector{Bool}`: 各点の失敗が許可されているかを示すベクトル。
  * `point_sets::Dict{Symbol,Vector{Int}}`: 点セットを含む辞書。
  * `point_params::Vector{PointParameters}`: ボディのすべての異なる点パラメータインスタンスを含むベクトル。各点は独自の `PointParameters` インスタンスを持つことができます。
  * `params_map::Vector{Int}`: 各点インデックスを `point_params` のパラメータインスタンスにマッピングするベクトル。
  * `single_dim_bcs::Vector{SingleDimBC}`: 単一次元の境界条件を持つベクトル。
  * `posdep_single_dim_bcs::Vector{PosDepSingleDimBC}`: 単一次元の位置依存境界条件を持つベクトル。
  * `single_dim_ics::Vector{SingleDimIC}`: 単一次元の初期条件を持つベクトル。
  * `posdep_single_dim_ics::Vector{PosDepSingleDimIC}`: 単一次元の位置依存初期条件を持つベクトル。
  * `data_bcs::Vector{DataBC}`: データ境界条件を持つベクトル。
  * `point_sets_precracks::Vector{PointSetsPreCrack}`: 事前定義された点セット亀裂を持つベクトル。
