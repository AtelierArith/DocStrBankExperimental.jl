```
BasisSet
```

原子の配列に関連付けられた一連の BasisFunction オブジェクトを保持するオブジェクトです。

# フィールド

| 名前         | 型                               | 説明                                       |
|:---------- |:------------------------------- |:---------------------------------------- |
| `atoms`    | `Vector{Atom}`                  | `Molecules.Atom` オブジェクトの配列               |
| `name`     | `String`                        | 基底セット名を保持する文字列                           |
| `basis`    | `Vector{Vector{BasisFunction}}` | BasisFunction を持つ配列の配列                   |
| `natoms`   | `Int32`                         | BasisSet 内の原子の数                          |
| `nbas`     | `Int32`                         | 基底関数の数（注意、BasisFunction オブジェクトの数とは等しくない） |
| `nshells`  | `Int32`                         | シェルの数、すなわち BasisFunction オブジェクト          |
| `lc_atoms` | `Array{Int32,1}`                | libcint にデータをマッピングする整数配列                 |
| `lc_bas`   | `Array{Int32,1}`                | libcint にデータをマッピングする整数配列                 |
| `lc_env`   | `Array{Float64,1}`              | libcint にデータをマッピングする Float64 配列          |

# 例

デフォルトオプションから基底セットを構築する

```julia
julia> water = Molecules.parse_string(
"O        1.2091536548      1.7664118189     -0.0171613972
 H        2.1984800075      1.7977100627      0.0121161719
 H        0.9197881882      2.4580185570      0.6297938832"
)
julia> bset = BasisSet("sto-3g", water)
sto-3g Basis Set
Number of shells: 5
Number of basis:  7

O: 1s 2s 1p 
H: 1s 
H: 1s
```

BasisSet オブジェクトは二次元配列としてアクセスできます。

```julia
julia> bset[1,2] # 最初の原子 (O 2s) の二番目の基底を表示
S シェルは 3 つの原始ガウスから構築された 1 基底を持つ

χ₀₀  =    0.8486970052⋅Y₀₀⋅exp(-5.033151319⋅r²)
     +    1.1352008076⋅Y₀₀⋅exp(-1.169596125⋅r²)
     +    0.8567529838⋅Y₀₀⋅exp(-0.38038896⋅r²)
```

自分自身のクレイジーなミックスを作成することもできます！ H のために 1 つの S と 1 つの P 基底関数を作成しましょう。

```julia
julia> h2 = Molecules.parse_string(
   "H 0.0 0.0 0.0
    H 0.0 0.0 0.7"
)
julia> s = BasisFunction(0, [0.5215367271], [0.122])
julia> p = BasisFunction(1, [1.9584045349], [0.727])
```

基底セットは原子の配列 (Vector{Atom}) と、その特定の原子のすべての基底関数を保持する対応する配列の Vector{BasisFunction} で構成されます。この例では、H₂ 分子の 2 つの原子に対して不均等な扱いを考慮します。

```
julia> shells = [
    [s],  # 最初の水素に対する s 関数
    [s,p] # 2 番目の水素に対する 1 つの s と 1 つの p 関数
]
julia> BasisSet("UnequalHydrogens", h2, shells)
UnequalHydrogens Basis Set
Number of shells: 3
Number of basis:  5

H: 1s 
H: 1s 1p
```
