```
genBasisFunc(center::Union{AbstractVector{T}, Tuple{Vararg{T}}, SpatialPoint, Missing}, 
             args..., kws...) where {T<:Union{AbstractFloat, ParamBox}} -> 
Union{FloatingGTBasisFuncs{T}, Vector{<:FloatingGTBasisFuncs{T}}}
```

`FloatingGTBasisFuncs`のコンストラクタですが、入力引数に基づいて異なる種類のコレクション（`Vector`）も返します。最初の引数`center`は生成される`FloatingGTBasisFuncs`の中心座標を指定し、後で代入するために`missing`のままにしておくことができます。

**注意:** 戻り値の型にはマークされていませんが、許可された入力引数のいずれかが内部に`GaussFunc`を持たない`FloatingGTBasisFuncs`を生成する場合、例えば`genBasisFunc([1.0, 2.0, 3.0], ())`のように、代わりに`Quiqbox.EmptyBasisFunc`が生成されます。

≡≡≡ メソッド 1 ≡≡≡

```
genBasisFunc(center, GsOrCoeffs, Ls; normalizeGTO=false) -> 
FloatingGTBasisFuncs
```

=== 位置引数 ===

`GsOrCoeffs::Union{     AbstractGaussFunc{T1},      AbstractVector{<:AbstractGaussFunc{T1}},      Tuple{Vararg{AbstractGaussFunc{T1}}},      NTuple{2, Union{T1, Array{T1, 0}, ParamBox{T1}},      NTuple{2, AbstractVector{<:Union{T1, Array{T1, 0}, ParamBox{T1}}}} } where {T1<:AbstractFloat}`: 基底関数を構築するために使用される同心の`GaussFunc`のコレクション。手続きを簡素化するために、`GaussFunc`の指数係数`::Union{AbstractFloat,  AbstractVector{<:AbstractFloat}}`と収束係数`::Union{AbstractFloat,  AbstractVector{<:AbstractFloat}}`の`NTuple{2}`の形でも指定できます。

`Ls::Union{     T2,      AbstractVector{T2},      NTuple{<:Any, T2} } where {T2<:Union{NTuple{D, Int}, LTuple{D}} where {D}}`: 同じサブシェル内の少なくとも1つの角運動量構成のコレクション。直交座標表現で指定します。例えば、pシェルの場合は`((1,0,0), (0,1,0))`と設定できます。これにより、出力される`FloatingGTBasisFuncs`に格納される空間軌道の数とその角運動量が決まります。

=== キーワード引数 ===

`normalizeGTO::Bool`: 計算中に内部の`GaussFunc`が正規化されるかどうかを決定します。

=== 例 ===

```jldoctest; setup = :(push!(LOAD_PATH, "../../src/"); using Quiqbox)
julia> genBasisFunc([0.,0.,0.], GaussFunc(2., 1.), (0, 1, 0))
BasisFunc{Float64, 3, 1, 1, …}{0, 0, 0}[(0.0, 0.0, 0.0)][X⁰Y¹Z⁰]
```

≡≡≡ メソッド 2 ≡≡≡

```
genBasisFunc(center, GsOrCoeffs, subshell="s"; normalizeGTO=false) -> 
FloatingGTBasisFuncs

genBasisFunc(center, GsOrCoeffs, subshell, lFilter; normalizeGTO=false) -> 
FloatingGTBasisFuncs
```

=== 位置引数 ===

`subshell::Union{String, Symbol}`: コンストラクタの第3引数はサブシェルの名前でもあり、出力がサブシェルを完全に占有する空間軌道を含む`BasisFuncs`であることを保証します。

`lFilter::Tuple{Vararg{Bool}}`: この4番目の引数が提供されると、指定された`subshell`に基づいて含める軌道を決定できます。対応する軌道角運動量の順序は、関数`orbitalLin`を使用して確認できます。

=== キーワード引数 ===

`normalizeGTO::Bool`: メソッド1で定義されたものと同じです。

=== 例 ===

```jldoctest; setup = :(push!(LOAD_PATH, "../../src/"); using Quiqbox)
julia> genBasisFunc([0.,0.,0.], (2., 1.), "p")
BasisFuncs{Float64, 3, 1, 1, …}{0, 0, 0}[(0.0, 0.0, 0.0)][3/3]

julia> genBasisFunc([0.,0.,0.], (2., 1.5), "p", (true, false, true))
BasisFuncs{Float64, 3, 1, 1, …}{0, 0, 0}[(0.0, 0.0, 0.0)][2/3]
```

≡≡≡ メソッド 3 ≡≡≡

```
genBasisFunc(center, BSkey, atm="H"; unlinkCenter=false) -> 
Vector{<:FloatingGTBasisFuncs}
```

=== 位置引数 ===

`BSkey::String`: 既存の原子基底セットの名前。サポートされているオプションは`["STO-2G", "STO-3G", "STO-6G", "3-21G", "6-31G", "cc-pVDZ", "cc-pVTZ", "cc-pVQZ"]`です。

`atm::Union{String, Symbol}`: 選択した基底セットに対応する原子の名前。サポートされているオプションは`["H", "He", "Li", "Be", "B", "C", "N", "O", "F", "Ne", "Na", "Mg", "Al", "Si", "P", "S", "Cl", "Ar", "K", "Ca"]`です。

=== キーワード引数 ===

`unlinkCenter::Bool`: 構築された`FloatingGTBasisFuncs`の中心が互いにリンクされているかどうかを決定します。`true`に設定すると、各`FloatingGTBasisFuncs`の中心は互いの`Base.deepcopy`になります。そうでない場合、同じ基礎データを共有するため、一方の値を変更すると他に影響を与えます。

=== 例 ===

```jldoctest; setup = :(push!(LOAD_PATH, "../../src/"); using Quiqbox)
julia> genBasisFunc([0.,0.,0.], "6-31G");

julia> genBasisFunc([0.,0.,0.], "STO-3G", "Li");
```

≡≡≡ メソッド 4 ≡≡≡

```
genBasisFunc(b::FloatingGTBasisFuncs{T, D}, newFieldVal) where {T, D} -> 
FloatingGTBasisFuncs{T, D}
```

=== 位置引数 ===

`newFieldVal::Union{     SpatialPoint{T, D},      Tuple{AbstractGaussFunc{T}, Vararg{AbstractGaussFunc{T}}},      Tuple{LTuple{D, 𝑙}, Vararg{LTuple{D, 𝑙}}} where 𝑙,      Bool } where {T<:AbstractFloat, D}`: `FloatingGTBasisFuncs`内の`param`以外の任意のフィールド。

このメソッドは、入力と同じフィールドを持つ`FloatingGTBasisFuncs`を出力しますが、`newFieldVal`によって置き換えられるフィールド（および置き換えられたフィールドが[`ParamBox`](@ref)を含む場合は`param`）を除きます。

=== 例 ===

```jldoctest; setup = :(push!(LOAD_PATH, "../../src/"); using Quiqbox)
julia> bf1 = genBasisFunc([1., 2., 3.], (2.0, 1.0), (0, 0, 0));

julia> bf2 = genBasisFunc([1., 2., 3.], (2.0, fill(1.0)), (0, 0, 1));

julia> bf1 = genBasisFunc(bf1, bf2.l);

julia> hasEqual(bf1, bf2)
true
```
