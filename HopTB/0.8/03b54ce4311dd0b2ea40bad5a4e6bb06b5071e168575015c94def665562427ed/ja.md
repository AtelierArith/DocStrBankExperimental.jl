`TBModel{T<Number}`は、タイトバインディングモデルを表すデータ型です。

# フィールド

  * `norbits::Int64`: モデル内のオービタルの数
  * `lat::SMatrix{3,3,Float64,9}`: 列に格納された原始格子ベクトル
  * `rlat::SMatrix{3,3,Float64,9}`: 列に格納された原始逆格子ベクトル
  * `hoppings::Dict{SVector{3,Int16},Matrix{T}}`: R -> ⟨0n|H|Rm⟩、ここでnは最初のインデックス、mは2番目のインデックスです。
  * `overlaps::Dict{SVector{3,Int16},Matrix{T}}`: R -> ⟨0n|Rm⟩
  * `positions::Dict{SVector{3,Int16},SVector{3,Matrix{T}}}`: R -> [⟨0n|rx|Rm⟩, ⟨0n|ry|Rm⟩, ⟨0n|rz|Rm⟩]
  * `isorthogonal`: モデルの異なるオービタルが互いに直交しているかどうか。
  * `nsites::Union{Missing,Int16}`: オービタルがいくつかのサイトにグループ化される可能性があります。すべてのオービタルのグループは、`site_positions`に格納されたグループ内の同じ位置を共有する必要があります。
  * `site_norbits::Union{Missing,Vector{Int64}}`: 各サイトのオービタルの数。
  * `site_positions::Union{Missing,Matrix{Float64}}`: 列に格納されたサイトの位置
  * `orbital_types::Union{Missing,Vector{Vector{Int16}}}`: オービタルが特定の対称性表現を持つ可能性があります。例: `orbital_types = [[0], [0, 1]]`は、2つのサイトがあり、最初のサイトには1つのsオービタルがあり、2番目のサイトには1つのsオービタルと1つのpオービタル（スピンを考慮しない合計4つのオービタル）があることを示します。TBModelのオービタルは、`orbital_types`によって示される一貫した順序で表示される必要があります。
  * `isspinful::Union{Missing,Bool}`: TBModelがスピンを持つ場合、オービタルの前半はスピンアップで、後半はスピンダウンである必要があります。オービタルの2つの半分は一対一の対応を持つ必要があります。
  * `is_canonical_ordered::Union{Missing,Bool}`: オービタルタイプが知られていて、`is_canonical_ordered`がtrueの場合、オービタルはLz値が減少する順序で表示されることが保証されます。例えば、pオービタルの標準順序は-px-i*py, pz, px-i*pyであるべきです。他のオービタルについてはウィキペディアを参照してください。

# 欠損データ

TBModelのすべてのフィールドが有効な値を持つ必要はありません。例えば、いくつかのモデルではサイト情報が欠けている可能性があります。以下は幾つかのルールです：

  * `nsites`、`site_norbits`、`site_positions`はすべて欠損または有効である必要があります。
  * `orbital_types`は、`nsites`、`site_norbits`、`site_positions`が有効な場合にのみ有効であることができます。
  * `is_canonical_ordered`は、`orbital_types`が有効な場合にのみ有効であることができます。

# 一貫性チェック

TBModelを直接変更する関数は、常に以下の一貫性を維持する必要があります（関連するフィールドが欠損していない場合）：

  * `hoppings`、`overlaps`および`positions`の行列は常にエルミートである必要があります。
  * `overlap[[0, 0, 0]]`は常に正定値である必要があります。
  * `diag(position[[0, 0, 0]][α])/diag(overlap[[0, 0, 0]])`は`site_positions`と一貫している必要があります。
  * オービタルの数は一貫している必要があります。
