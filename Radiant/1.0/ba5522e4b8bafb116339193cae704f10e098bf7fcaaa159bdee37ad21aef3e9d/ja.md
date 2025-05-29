```
Discrete_Ordinates
```

粒子輸送に関連する離散化手法を定義するために使用される構造体。

# 必須フィールド

  * `particle::Particle` : 離散化手法が定義される粒子
  * `solver_type::String` : 輸送計算のためのソルバーの種類。
  * `quadrature_type::String` : 角度領域のための数値積分の種類。
  * `quadrature_order::Int64` : 角度領域のための数値積分の次数。
  * `legendre_order::Int64` : 微分断面積のためのレジェンドル展開の最大次数。
  * `scheme_type::Dict{String,String}` : 空間またはエネルギーの離散化のためのスキームの種類。
  * `scheme_order::Dict{String,Int64}` : 離散化スキームのための展開の次数。

# オプションフィールド - デフォルト値付き

  * `angular_fokker_planck::String = "finite-difference"` : 角度フォッカー・プランク操作のための離散化の種類。
  * `angular_boltzmann::String = "galerkin-d"` : ボルツマン操作のための離散化の種類。
  * `convergence_criterion::Float64 = 1e-7` : グループ内反復の収束基準。
  * `maximum_iteration::Int64 = 300` : グループ内反復の最大回数。
  * `acceleration::Int64 = "none"` : グループ内反復のための加速手法。
