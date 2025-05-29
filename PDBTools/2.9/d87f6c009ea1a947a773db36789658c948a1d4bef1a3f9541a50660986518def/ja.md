```
Atom::DataType
```

原子のプロパティを含む構造体です。可変であるため、そのフィールドは変更可能です。

フィールド:

```
mutable struct Atom{CustomType}
    index::Int32 # ファイル内の原子の連続インデックス
    index_pdb::Int32 # PDBファイルに記載されたインデックス（何でもあり得る）
    name::String7 # 原子名
    resname::String7 # 残基名
    chain::String3 # チェーン識別子
    resnum::Int32 # PDBファイルに記載された残基番号
    residue::Int32 # ファイル内の連続残基（分子）番号
    x::Float32 # x座標
    y::Float32 # y座標
    z::Float32 # z座標
    beta::Float32 # 温度因子
    occup::Float32 # 占有率
    model::Int32 # モデル番号
    segname::String7 # セグメント名（列 73:76）
    pdb_element::String3 # 元素記号文字列（列 77:78）
    charge::Float32 # 電荷（列: 79:80）
    custom::CustomType # カスタムフィールド
    flag::Int8 # 内部使用のフラグ
end
```

### 例

```jldoctest
julia> using PDBTools

julia> atoms = read_pdb(PDBTools.SMALLPDB)
   Vector{Atom{Nothing}} with 35 atoms with fields:
   index name resname chain   resnum  residue        x        y        z occup  beta model segname index_pdb
       1    N     ALA     A        1        1   -9.229  -14.861   -5.481  0.00  0.00     1    PROT         1
       2 1HT1     ALA     A        1        1  -10.048  -15.427   -5.569  0.00  0.00     1    PROT         2
⋮
      34    C     ASP     A        3        3   -2.626  -10.480   -7.749  1.00  0.00     1    PROT        34
      35    O     ASP     A        3        3   -1.940  -10.014   -8.658  1.00  0.00     1    PROT        35

julia> resname(atoms[1])
"ALA"

julia> chain(atoms[1])
"A"

julia> element(atoms[1])
"N"

julia> mass(atoms[1])
14.0067

julia> position(atoms[1])
3-element StaticArraysCore.SVector{3, Float32} with indices SOneTo(3):
  -9.229
 -14.861
  -5.481
```

`pdb_element` および `charge` フィールドは、PDBファイルで頻繁に空のままにされるため、表示されません。フィールドへの直接アクセスはインターフェースの一部と見なされます。

カスタムフィールドは、`custom` キーワード引数を使用して `Atom` の構築時に設定できます。Atom構造体は、その後 `custom` の型でパラメータ化されます。

### 例

```jldoctest
julia> using PDBTools

julia> atom = Atom(index = 0; custom=Dict(:c => "c", :index => 1));

julia> typeof(atom)
Atom{Dict{Symbol, Any}}

julia> atom.custom
Dict{Symbol, Any} with 2 entries:
  :index => 1
  :c     => "c"

julia> atom.custom[:c]
"c"
```
