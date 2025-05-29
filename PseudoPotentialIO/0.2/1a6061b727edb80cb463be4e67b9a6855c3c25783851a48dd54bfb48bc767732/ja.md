```julia
abstract type AbstractPsP
```

擬ポテンシャルを表す抽象型。

データの構造は効率的な計算を促進するべきです。

必要なメソッド：

```julia
# 一意の文字列、通常はハッシュまたはチェックサム。
function identifier(file::AbstractPsP)::AbstractString end
# 擬ポテンシャルが構築される元素の記号（例：`"Ag"`）
function elemental_symbol(psp::AbstractPsP)::AbstractString end
# 最大角運動量チャネル
function max_angular_momentum(psp::AbstractPsP)::Integer end
# 角運動量 `l` に対する非局所プロジェクタの放射状部分の数
function n_projector_radials(psp::AbstractPsP, l::Integer)::Integer end
# 角運動量 `l` に対するカイ関数の放射状部分の数
function n_chi_function_radials(psp::AbstractPsP, l::Integer)::Integer end
# 擬原子価電子の電荷
function valence_charge(psp::AbstractPsP)::Real end
# 擬化された原子の電荷（例：酸素のための8）
function atomic_charge(psp::AbstractPsP)::Real end
# 擬ポテンシャルがノルム保存型擬ポテンシャルであるかどうか
function is_norm_conserving(psp::AbstractPsP)::Bool end
# 擬ポテンシャルがウルトラソフト擬ポテンシャルであるかどうか
function is_ultrasoft(psp::AbstractPsP)::Bool end
# 擬ポテンシャルがプロジェクタ強化波擬ポテンシャルであるかどうか
function is_paw(psp::AbstractPsP)::Bool end
# 擬ポテンシャルがスピン軌道結合計算をサポートしているかどうか
function has_spin_orbit(psp::AbstractPsP)::Bool end
# 擬ポテンシャルがコア電荷密度を含んでいるかどうか（すなわち、非線形コア補正をサポート）
function has_core_density(psp::AbstractPsP)::Bool end
# 擬ポテンシャルが価電子密度を含んでいるかどうか（すなわち、特別な推測電荷密度の構築をサポート）
function has_valence_density(psp::AbstractPsP)::Bool end
# 擬ポテンシャルが価電子のためのカイ関数を含んでいるかどうか（すなわち、特別な軌道投影量の計算をサポート）
function has_chi_functions(psp:AbstractPsP)::Bool end
# 角運動量 `l` に対するプロジェクタ結合係数
function projector_coupling(psp::AbstractPsP, l::Integer)::Matrix{Real} end
# 局所ポテンシャルが許容誤差 `tol` 内でゼロに減衰する放射距離
function local_potential_cutoff_radius(psp::AbstractPsP; tol) end
# 角運動量 `l` における `n` 番目の非局所プロジェクタが許容誤差 `tol` 内でゼロに減衰する放射距離
function projector_cutoff_radius(psp::AbstractPsP, l, n; tol) end
# 角運動量 `l` における `n` 番目のカイ関数が許容誤差 `tol` 内でゼロに減衰する放射距離
function chi_function_cutoff_radius(psp::AbstractPsP, l, n; tol) end
# 価電子密度が許容誤差 `tol` 内でゼロに減衰する放射距離
function valence_charge_density_cutoff_radius(psp::AbstractPsP; tol) end
# コア電荷密度が許容誤差 `tol` 内でゼロに減衰する放射距離
function core_charge_density_cutoff_radius(psp::AbstractPsP; tol) end
# 実空間の放射座標で局所ポテンシャルを評価する関数を返す
function local_potential_real(psp::AbstractPsP) end
# 実空間の放射座標で角運動量 `l` の `n` 番目の非局所プロジェクタを評価する関数を返す
function projector_real(psp::AbstractPsP, l, n) end
# 実空間の放射座標で角運動量 `l` の `n` 番目のカイ関数を評価する関数を返す
function chi_function_real(psp::AbstractPsP, l, n) end
# 実空間の放射座標で価電子密度を評価する関数を返す
function valence_charge_density_real(psp::AbstractPsP) end
# 実空間の放射座標でコア電荷密度を評価する関数を返す
function core_charge_density_real(psp::AbstractPsP) end
# フーリエ空間の放射座標で局所ポテンシャルを評価する関数を返す
function local_potential_fourier(psp::AbstractPsP) end
# フーリエ空間の放射座標で角運動量 `l` の `n` 番目の非局所プロジェクタを評価する関数を返す
function projector_fourier(psp::AbstractPsP, l, n) end
# フーリエ空間の放射座標で角運動量 `l` の `n` 番目のカイ関数を評価する関数を返す
function chi_function_fourier(psp::AbstractPsP, l, n) end
# フーリエ空間の放射座標で価電子密度を評価する関数を返す
function valence_charge_density_fourier(psp::AbstractPsP) end
# フーリエ空間の放射座標でコア電荷密度を評価する関数を返す
function core_charge_density_fourier(psp::AbstractPsP) end
# 擬ポテンシャルエネルギー補正
function pseudo_energy_correction(psp::AbstractPsP) end
```
