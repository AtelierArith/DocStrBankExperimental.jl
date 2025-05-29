```
ScalarPSF{T} <: Abstract3DPSF{T}
```

明示的な瞳孔関数表現を使用したスカラー3D PSF。

# フィールド

  * `nₐ::T`: 数値開口
  * `λ::T`: 波長（マイクロメートル単位）
  * `n::T`: 屈折率
  * `pupil::PupilFunction{T}`: 複素瞳孔関数
  * `zernike_coeffs::Union{Nothing, ZernikeCoefficients{T}}`: このPSFを作成するために使用されるゼルニケ係数（該当する場合）

# ノート

ScalarPSFファクトリ関数を使用して、PupilFunctionまたはZernikeCoefficientsのいずれかで初期化できます。
