タイプ: NLPAtX

メソッド: update!, reinit!

NLPAtXは、反非線形最適化モデルに関する情報をイテレートxで保持します。

min_{x ∈ ℜⁿ} f(x) subject to lcon <= c(x) <= ucon, lvar <= x <= uvar.

追跡データには以下が含まれます:

  * x             : 現在のイテレート
  * fx [opt]      : xでの関数評価
  * gx [opt]      : xでの勾配評価
  * Hx [opt]      : xでのヘッセ行列評価
  * mu [opt]      : 制約の境界条件のラグランジュ乗数
  * cx [opt]      : xでの制約関数の評価
  * Jx [opt]      : xでの制約関数のヤコビ行列
  * lambda        : 制約のラグランジュ乗数
  * d [opt]       : 探索方向
  * res [opt]     : 残差
  * current_time  : 時間
  * current_score : スコア

(import the type NLPModels.Counters)

コンストラクタ:  `NLPAtX(:: T, :: T, :: S; fx :: eltype(T) = _init_field(eltype(T)), gx :: T = _init_field(T), Hx :: Matrix{eltype(T)} = _init_field(Matrix{eltype(T)}), mu :: T = _init_field(T), cx :: T = _init_field(T), Jx :: SparseMatrixCSC{eltype(T), Int64} = _init_field(SparseMatrixCSC{eltype(T), Int64}), d :: T = _init_field(T), res :: T = _init_field(T), current_time :: Float64 = NaN) where {S, T <: AbstractVector}`

`NLPAtX(:: T; fx :: eltype(T) = _init_field(eltype(T)), gx :: T = _init_field(T), Hx :: Matrix{eltype(T)} = _init_field(Matrix{eltype(T)}), mu :: T = _init_field(T), current_time :: Float64 = NaN, current_score :: Union{T,eltype(T)} = _init_field(eltype(T))) where {T <: AbstractVector}`

`NLPAtX(:: T, :: T; fx :: eltype(T) = _init_field(eltype(T)), gx :: T = _init_field(T), Hx :: Matrix{eltype(T)} = _init_field(Matrix{eltype(T)}), mu :: T = _init_field(T), cx :: T = _init_field(T), Jx :: SparseMatrixCSC{eltype(T), Int64} = _init_field(SparseMatrixCSC{eltype(T), Int64}), d :: T = _init_field(T), res :: T = _init_field(T), current_time :: Float64  = NaN, current_score :: Union{T,eltype(T)} = _init_field(eltype(T))) where T <: AbstractVector`

注意:

  * デフォルトでは、未知のエントリは`_init_field`を使用して設定されます。
  * デフォルトで`current_score`の型は`eltype(x)`であり、ステートが作成されると変更できません。長さnのベクトル化された`current_score`を持つには、`GenericState(x, Array{eltype(x),1}(undef, n))`のようなものを試してください。
  * これらの情報（`x`と`lambda`を除く）はすべてオプショナルであり、必要に応じて更新する必要があります。更新は`update!`関数を通じて行われます。
  * `x`と`lambda`は必須のエントリです。制約がない場合は`lambda = []`。
  * コンストラクタはエントリのサイズをチェックします。

参照: `GenericState`, `update!`, `update_and_start!`, `update_and_stop!`, `reinit!`
