```
mul(a1::Real, a2::CompositeGTBasisFuncs{T, D, <:Any, 1}; 
    normalizeGTO::Union{Bool, Missing}=missing, 
    roundAtol::Real=getAtolVal(T)) where {T, D} -> 
CompositeGTBasisFuncs{T, D, <:Any, 1}

mul(a1::CompositeGTBasisFuncs{T, D, <:Any, 1}, a2::Real; 
    normalizeGTO::Union{Bool, Missing}=missing, 
    roundAtol::Real=getAtolVal(T)) where {T, D} -> 
CompositeGTBasisFuncs{T, D, <:Any, 1}

mul(a1::CompositeGTBasisFuncs{T, D, <:Any, 1}, 
    a2::CompositeGTBasisFuncs{T, D, <:Any, 1}; 
    normalizeGTO::Union{Bool, Missing}=missing, 
    roundAtol::Real=getAtolVal(T)) where {T, D} -> 
CompositeGTBasisFuncs{T, D, <:Any, 1}

二つの `CompositeGTBasisFuncs{T, D, <:Any, 1}`（例： [`BasisFunc`](@ref) と [`BasisFuncMix`](@ref)）または `Real` 数と `CompositeGTBasisFuncs{T, D, <:Any, 1}` の間の乗算。 `normalizeGTO` が `missing`（デフォルト）に設定されている場合、出力コンテナ内の [`GaussFunc`](@ref) は、すべての入力 `FloatingGTBasisFuncs`（または入力 `CompositeGTBasisFuncs` 内）に `hasNormFactor(ai) == true` が保持されている場合にのみ正規化されます。 `roundAtol` は、各 `CompositeGTBasisFuncs` に格納されているパラメータを比較して「等しい」と見なされるかどうかを判断するための絶対近似許容誤差を指定します。返される `CompositeGTBasisFuncs` の各パラメータは、`0.5atol` の最も近い正確な倍数に設定されます。 `roundAtol` が `NaN` に設定されている場合、近似や丸めは行われません。この関数は、キーワード引数がデフォルト値に設定された状態で `*` 構文を使用して呼び出すことができます。

≡≡≡ 例 ≡≡≡

```

jldoctest; setup = :(push!(LOAD_PATH, "../../src/"); using Quiqbox) julia> bf1 = genBasisFunc([1.0, 1.0, 1.0], ([2.0, 1.0], [0.1, 0.2]));

julia> gaussCoeffOf(bf1) 2×2 Matrix{Float64}:  2.0  0.1  1.0  0.2

julia> bf2 = bf1 * 2;

julia> gaussCoeffOf(bf2) 2×2 Matrix{Float64}:  2.0  0.2  1.0  0.4

julia> bf3 = bf1 * bf2;

julia> gaussCoeffOf(bf3) 3×2 Matrix{Float64}:  4.0  0.02  3.0  0.08  2.0  0.08

```

```
