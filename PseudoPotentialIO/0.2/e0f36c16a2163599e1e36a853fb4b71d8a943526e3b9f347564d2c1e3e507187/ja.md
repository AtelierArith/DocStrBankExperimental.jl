```julia
abstract type PsPFile
```

擬ポテンシャルファイルを表す抽象型。

データの構造はファイルの形式に密接に対応している必要があり、量の値はファイルに見られるものと正確に一致する必要があります。

必要なメソッド：

```julia
# 一意の文字列、通常はハッシュまたはチェックサム。
function identifier(file::PsPFile)::AbstractString end
# ファイル形式を示す短い文字列（例：`"PSP8"`）
function format(file::PsPFile)::AbstractString end
# ファイルが擬ポテンシャルを含む元素の記号（例：`"Ag"`）
function elemental_symbol(file::PsPFile)::AbstractString end
# ファイルに含まれる最大角運動量チャネル
function max_angular_momentum(file::PsPFile)::Integer end
# ファイルに含まれる角運動量 `l` のための非局所プロジェクターの数
function n_projector_radials(file::PsPFile, l::Integer)::Integer end
# ファイルに含まれる角運動量 `l` のためのカイ関数の数
function n_chi_function_radials(file::PsPFile, l::Integer)::Integer end
# 擬原子価電子密度
function valence_charge(file::PsPFile)::Real end
# ファイルがノルム保存型擬ポテンシャルを含むかどうか
function is_norm_conserving(file::PsPFile)::Bool end
# ファイルがウルトラソフト擬ポテンシャルを含むかどうか
function is_ultrasoft(file::PsPFile)::Bool end
# ファイルがプロジェクター拡張波擬ポテンシャルを含むかどうか
function is_paw(file::PsPFile)::Bool end
# ファイルがスピン軌道結合計算をサポートする擬ポテンシャルを含むかどうか
function has_spin_orbit(file::PsPFile)::Bool end
# ファイルが非線形コア補正をサポートする擬ポテンシャルを含むかどうか
function has_core_density(file::PsPFile)::Bool end
```
