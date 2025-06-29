```
qnm_kerr(a, s, l, m, ω_guess; kwargs...)
```

Kerr QNMをLeaverの方法を使用して放射方程式を解き、Cook-Zalutskiyアプローチを使用して角度セクターを解きます。単位$M = G = c = 1$を使用します。

# 引数

  * `a`: ケルパラメータ（無次元スピンパラメータ、0 ≤ |a| ≤ 1）
  * `s`: フィールドのスピン重み（重力摂動の場合は±2、電磁摂動の場合は±1、スカラー摂動の場合は0）
  * `l`: 角運動量量子数（l ≥ |s|）
  * `m`: 方位ハーモニックインデックス（-l ≤ m ≤ l）
  * `ω_guess`: QNM周波数の初期推定値

# キーワード引数

  * `n`: オーバートーン数（デフォルト: 基本モードの場合は0）
  * `A_guess`: 角度分離定数の初期推定値（デフォルト: なし）
  * `poles`: 続分数から引き算する既知の極のベクトル（デフォルト: 空）
  * `l_max`: 角度固有値計算のための最大角運動量（デフォルト: l + 20）
  * `cf_n_inv`: 続分数の逆項の数（デフォルト: 0）
  * `cf_N_min`: 続分数の最小項数（デフォルト: 300）
  * `cf_N_max`: 続分数の最大項数（デフォルト: 100000）
  * `cf_tol`: 続分数収束の許容誤差（デフォルト: マシンイプシロン）
  * `nonlinear_algorithm`: 非線形固有値問題を解くためのアルゴリズム（デフォルト: RobustMultiNewton with AutoFiniteDiff）
  * `angular_matrix_cache`: 角度固有値計算のための事前割り当て行列（デフォルト: なし）
  * `kwargs...`: 非線形ソルバーに渡される追加のキーワード引数

# 戻り値

  * `Complex{TF}`: 複素QNM周波数$\omega$

# 例

```julia
a = 0.7
s = 2
l = 2
m = 2
n = 0
ω = 0.532600243551018 - 0.08079287315500766im
l_max = 20

ω_pert = ω + rand(Complex{Float64}) / 1000

ωsol = qnm_kerr(a, s, l, m, ω_pert; n=n, l_max=l_max)
```

# 注意事項

  * この関数は、放射方程式に対してLeaverの方法と角度セクターに対してCook-Zalutskiyアプローチの組み合わせを使用します
  * 続分数法を使用して放射方程式を解きます
  * 角度固有値問題は行列固有値法を使用して解決されます
  * この関数は、虚部が負である複素周波数（減衰モード）を返します

```
