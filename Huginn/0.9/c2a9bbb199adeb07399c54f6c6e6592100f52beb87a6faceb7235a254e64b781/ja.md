```
mutable struct SIA2Dmodel{R <: Real, I <: Integer} <: SIAmodel
```

2D浅氷近似（SIA）モデルを表す可変構造体です。

# フィールド

  * `A::Union{Ref{R}, Nothing}`: 流量係数。
  * `n::Union{Ref{R}, Nothing}`: 流動法則の指数。
  * `C::Union{Ref{R}, Matrix{R}, Nothing}`: スライディング係数。
  * `H₀::Matrix{R}`: 初期氷厚。
  * `H::Union{Matrix{R}, Nothing}`: 氷厚。
  * `H̄::Union{Matrix{R}, Nothing}`: 平均氷厚。
  * `S::Matrix{R}`: 表面標高。
  * `dSdx::Union{Matrix{R}, Nothing}`: x方向の表面傾斜。
  * `dSdy::Union{Matrix{R}, Nothing}`: y方向の表面傾斜。
  * `D::Union{Matrix{R}, Nothing}`: 拡散率。
  * `D_is_provided::Union{Bool, Nothing}`: Dがユーザーによって提供されるか計算されるかを指定します。
  * `Dx::Union{Matrix{R}, Nothing}`: x方向の拡散率。
  * `Dy::Union{Matrix{R}, Nothing}`: y方向の拡散率。
  * `dSdx_edges::Union{Matrix{R}, Nothing}`: x方向のエッジでの表面傾斜。
  * `dSdy_edges::Union{Matrix{R}, Nothing}`: y方向のエッジでの表面傾斜。
  * `∇S::Union{Matrix{R}, Nothing}`: 表面標高の勾配。
  * `∇Sy::Union{Matrix{R}, Nothing}`: y方向の表面標高の勾配。
  * `∇Sx::Union{Matrix{R}, Nothing}`: x方向の表面標高の勾配。
  * `Fx::Union{Matrix{R}, Nothing}`: x方向のフラックス。
  * `Fy::Union{Matrix{R}, Nothing}`: y方向のフラックス。
  * `Fxx::Union{Matrix{R}, Nothing}`: x方向のフラックスの二次導関数。
  * `Fyy::Union{Matrix{R}, Nothing}`: y方向のフラックスの二次導関数。
  * `V::Union{Matrix{R}, Nothing}`: 速度。
  * `Vx::Union{Matrix{R}, Nothing}`: x方向の速度。
  * `Vy::Union{Matrix{R}, Nothing}`: y方向の速度。
  * `Γ::Union{Ref{R}, Nothing}`: 基底せん断応力。
  * `MB::Union{Matrix{R}, Nothing}`: 質量収支。
  * `MB_mask::Union{AbstractArray{Bool}, Nothing}`: 質量収支のマスク。
  * `MB_total::Union{Matrix{R}, Nothing}`: 総質量収支。
  * `glacier_idx::Union{Ref{I}, Nothing}`: 氷河のインデックス。
