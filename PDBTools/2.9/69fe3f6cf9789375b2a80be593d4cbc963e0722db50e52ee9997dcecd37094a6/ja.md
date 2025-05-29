```
contact_map(
    atoms1::AbstractVector{<:PDBTools.Atom}
    atoms2::AbstractVector{<:PDBTools.Atom}; # 2つの構造間の接触のためのオプション
    dmax::Real=4.0,
    gap::Int=0, # atoms2が提供されていない場合のみ利用可能
    unitcell=nothing,
    discrete::Bool=true,
    positions::Union{Nothing,AbstractVector{<:AbstractVector{<:Real}}}=nothing,
)

タンパク質*構造内の残基間の接触マップを計算します（`atoms1`のみが提供されている場合）または2つの異なるタンパク質*構造内の残基間の接触マップを計算します（`atoms1`と`atoms2`）。

!!! note
    接触を定義するために使用される距離は、提供された原子群の残基の任意の2つの原子間の**最小**距離であり、しきい値距離`dmax`があります。

接触マップを`ContactMap`オブジェクトとして返します。

*「タンパク質」という用語は、残基を持つ任意の構造を指すために使用されます。

# 引数

  * `atoms1::AbstractVector{<:PDBTools.Atom}`: 最初の構造の原子。
  * `atoms2::AbstractVector{<:PDBTools.Atom}`: 提供されている場合の2番目の構造の原子。

# オプションのキーワード引数

  * `dmax::Real=4.0`: 接触のためのしきい値距離。
  * `gap::Int=0`: 接触を計算するための残基間のギャップ。
  * `unitcell=nothing`: 周期境界条件のための単位セルの寸法。
  * `discrete::Bool=true`: `true`の場合、行列は`Bool`値を含み、`true`は接触を示し、`false`は接触がないことを示します。`false`の場合、行列は残基間の距離を含みます。
  * `positions`: 構造内の原子の位置。提供されている場合、関数はこれらの位置を使用して残基間の距離を計算します。

# 例

## 同じ構造内の残基間の接触マップ

```

jldoctest julia> using PDBTools

julia> ats = read_pdb(PDBTools.DIMERPDB);

julia> cA = select(ats, "chain A");

julia> cB = select(ats, "chain B");

julia> map = contact_map(cA, cB) # チェーンAとBの接触マップ ContactMap{Union{Missing, Bool}} of size (243, 12), with threshold 4.0 and gap 0 

julia> # using Plots; heatmap(map); # 接触マップをプロットするにはコメントを外してください

```

## 2つの異なる構造間の残基間の接触マップ

```

jldoctest julia> using PDBTools

julia> ats = read_pdb(PDBTools.DIMERPDB);

julia> cA = select(ats, "chain A");

julia> cB = select(ats, "chain B");

julia> map = contact_map(cA, cB) # チェーンAとBの接触マップ ContactMap{Union{Missing, Bool}} of size (243, 12), with threshold 4.0 and gap 0 

julia> # using Plots; heatmap(map); # 接触マップをプロットするにはコメントを外してください ```
