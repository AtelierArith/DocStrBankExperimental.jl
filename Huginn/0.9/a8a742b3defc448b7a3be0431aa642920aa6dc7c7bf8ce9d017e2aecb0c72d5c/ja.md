```
SIA2Dmodel(
    params::Sleipnir.Parameters;
    A::Union{R, Nothing} = nothing,
    n::Union{R, Nothing} = nothing,
    C::Union{R, Matrix{R}, Nothing} = nothing,
    H₀::Matrix{R} = Matrix{Sleipnir.Float}([;;]),
    H::Union{Matrix{R}, Nothing} = nothing,
    H̄::Union{Matrix{R}, Nothing} = nothing,
    S::Matrix{R} = Matrix{Sleipnir.Float}([;;]),
    dSdx::Union{Matrix{R}, Nothing} = nothing,
    dSdy::Union{Matrix{R}, Nothing} = nothing,
    D::Union{Matrix{R}, Nothing} = nothing,
    D_is_provided::Union{Bool, Nothing} = nothing,
    Dx::Union{Matrix{R}, Nothing} = nothing,
    Dy::Union{Matrix{R}, Nothing} = nothing,
    dSdx_edges::Union{Matrix{R}, Nothing} = nothing,
    dSdy_edges::Union{Matrix{R}, Nothing} = nothing,
    ∇S::Union{Matrix{R}, Nothing} = nothing,
    ∇Sy::Union{Matrix{R}, Nothing} = nothing,
    ∇Sx::Union{Matrix{R}, Nothing} = nothing,
    Fx::Union{Matrix{R}, Nothing} = nothing,
    Fy::Union{Matrix{R}, Nothing} = nothing,
    Fxx::Union{Matrix{R}, Nothing} = nothing,
    Fyy::Union{Matrix{R}, Nothing} = nothing,
    V::Union{Matrix{R}, Nothing} = nothing,
    Vx::Union{Matrix{R}, Nothing} = nothing,
    Vy::Union{Matrix{R}, Nothing} = nothing,
    Γ::Union{R, Nothing} = nothing,
    MB::Union{Matrix{R}, Nothing} = nothing,
    MB_mask::Union{BitMatrix, Nothing} = nothing,
    MB_total::Union{Matrix{R}, Nothing} = nothing,
    glacier_idx::Union{I, Nothing} = nothing
) where {I <: Integer, R <: Real}
```

指定されたパラメータを使用して新しい `SIA2Dmodel` オブジェクトを構築します。

# 引数

  * `params::Sleipnir.Parameters`: シミュレーションパラメータ。
  * `A::Union{R, Nothing}`: 流動法パラメータ（デフォルト: `nothing`）。
  * `n::Union{R, Nothing}`: 流動法指数（デフォルト: `nothing`）。
  * `C::Union{R, Matrix{R}, Nothing}`: 基底すべりパラメータ（デフォルト: `nothing`）。
  * `H₀::Matrix{R}`: 初期氷厚（デフォルト: 空の行列）。
  * `H::Union{Matrix{R}, Nothing}`: 氷厚（デフォルト: `nothing`）。
  * `H̄::Union{Matrix{R}, Nothing}`: 平均氷厚（デフォルト: `nothing`）。
  * `S::Matrix{R}`: 表面標高（デフォルト: 空の行列）。
  * `dSdx::Union{Matrix{R}, Nothing}`: x方向の表面傾斜（デフォルト: `nothing`）。
  * `dSdy::Union{Matrix{R}, Nothing}`: y方向の表面傾斜（デフォルト: `nothing`）。
  * `D::Union{Matrix{R}, Nothing}`: 拡散率（デフォルト: `nothing`）。
  * `D_is_provided::Union{Bool, Nothing}`: Dがユーザーによって提供されるか計算されるかを指定（デフォルト: `false`）。
  * `Dx::Union{Matrix{R}, Nothing}`: x方向の拡散率（デフォルト: `nothing`）。
  * `Dy::Union{Matrix{R}, Nothing}`: y方向の拡散率（デフォルト: `nothing`）。
  * `dSdx_edges::Union{Matrix{R}, Nothing}`: x方向のエッジでの表面傾斜（デフォルト: `nothing`）。
  * `dSdy_edges::Union{Matrix{R}, Nothing}`: y方向のエッジでの表面傾斜（デフォルト: `nothing`）。
  * `∇S::Union{Matrix{R}, Nothing}`: 表面標高の勾配（デフォルト: `nothing`）。
  * `∇Sy::Union{Matrix{R}, Nothing}`: y方向の表面標高の勾配（デフォルト: `nothing`）。
  * `∇Sx::Union{Matrix{R}, Nothing}`: x方向の表面標高の勾配（デフォルト: `nothing`）。
  * `Fx::Union{Matrix{R}, Nothing}`: x方向のフラックス（デフォルト: `nothing`）。
  * `Fy::Union{Matrix{R}, Nothing}`: y方向のフラックス（デフォルト: `nothing`）。
  * `Fxx::Union{Matrix{R}, Nothing}`: x方向のフラックスの二次導関数（デフォルト: `nothing`）。
  * `Fyy::Union{Matrix{R}, Nothing}`: y方向のフラックスの二次導関数（デフォルト: `nothing`）。
  * `V::Union{Matrix{R}, Nothing}`: 速度（デフォルト: `nothing`）。
  * `Vx::Union{Matrix{R}, Nothing}`: x方向の速度（デフォルト: `nothing`）。
  * `Vy::Union{Matrix{R}, Nothing}`: y方向の速度（デフォルト: `nothing`）。
  * `Γ::Union{R, Nothing}`: 補助行列（デフォルト: `nothing`）。
  * `MB::Union{Matrix{R}, Nothing}`: 質量収支（デフォルト: `nothing`）。
  * `MB_mask::Union{BitMatrix, Nothing}`: 質量収支のマスク（デフォルト: `nothing`）。
  * `MB_total::Union{Matrix{R}, Nothing}`: 総質量収支（デフォルト: `nothing`）。
  * `glacier_idx::Union{I, Nothing}`: 氷河のインデックス（デフォルト: `nothing`）。

# 戻り値

  * `SIA2Dmodel`: 新しい `SIA2Dmodel` オブジェクト。
