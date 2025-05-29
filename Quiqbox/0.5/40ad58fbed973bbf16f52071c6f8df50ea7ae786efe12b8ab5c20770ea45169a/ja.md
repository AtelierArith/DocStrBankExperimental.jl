```
mul(gf::GaussFunc{T}, coeff::Real; roundAtol::Real=getAtolVal(T)) where {T} -> 
GaussFunc

mul(coeff::Real, gf::GaussFunc{T}; roundAtol::Real=getAtolVal(T)) where {T} -> 
GaussFunc

mul(gf1::GaussFunc{T}, gf2::GaussFunc{T}; roundAtol::Real=getAtolVal(T)) where {T} -> 
GaussFunc
```

`Real` 数と [`GaussFunc`](@ref) または 2 つの `GaussFunc` の間の乗算。 `roundAtol` は、各 `GaussFunc` に格納されたパラメータを比較して「等しい」と見なされるかどうかを判断するための絶対近似許容誤差を指定します。返される `GaussFunc` の各パラメータは、最も近い正確な `0.5atol` の倍数に設定されます。 `roundAtol` が `NaN` に設定されている場合、近似や丸めは行われません。この関数は、キーワード引数をデフォルト値に設定して `*` 構文を使用して呼び出すことができます。

**注意:** 非微分可能としてマークされた入力引数に格納された `ParamBox` は、可能であれば融合され、新しい `ParamBox`(s) が生成され、もはやそれに格納されたデータ（入力変数）にリンクされなくなります。

≡≡≡ 例 ≡≡≡

```jldoctest; setup = :(push!(LOAD_PATH, "../../src/"); using Quiqbox)
julia> gf1 = GaussFunc(3.0, 1.0)
GaussFunc{Float64, …}{0, 0}[∂∂][{3.0, 1.0}]

julia> gf1 * 2
GaussFunc{Float64, …}{0, 0}[∂∂][{3.0, 2.0}]

julia> gf1 * gf1
GaussFunc{Float64, …}{0, 0}[∂∂][{6.0, 1.0}]

julia> gf1 * 2 * gf1
GaussFunc{Float64, …}{0, 0}[∂∂][{6.0, 2.0}]
```
