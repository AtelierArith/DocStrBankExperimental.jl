```
VectorPSF{T<:AbstractFloat} <: Abstract3DPSF{T}
```

明示的な瞳孔関数表現を使用したベクトルPSFモデル。カスタム収差のために瞳孔関数を直接操作することができます。

# フィールド

  * `nₐ::T`: 数値開口
  * `λ::T`: 波長（マイクロメートル単位）
  * `n_medium::T`: サンプル媒体の屈折率
  * `n_coverslip::T`: カバーガラスの屈折率
  * `n_immersion::T`: 没入媒体の屈折率
  * `dipole::DipoleVector{T}`: ダイポールの向き
  * `z_stage::T`: サンプルステージがカバーガラスの名目焦点面から移動した距離（μm）
  * `vector_pupils::Vector{VectorPupilFunction{T}}`: フィールド成分を含む瞳孔関数のベクトル。単一のダイポールの場合、これには1つの瞳孔が含まれます。回転するダイポールの場合、x、y、およびzの向きに対して3つの瞳孔が含まれます。
  * `base_pupil::Union{Nothing, PupilFunction{T}}`: システムの収差を表す基底瞳孔関数
  * `zernike_coeffs::Union{Nothing, ZernikeCoefficients{T}}`: このPSFを作成するために使用されるゼルニケ係数（該当する場合）
