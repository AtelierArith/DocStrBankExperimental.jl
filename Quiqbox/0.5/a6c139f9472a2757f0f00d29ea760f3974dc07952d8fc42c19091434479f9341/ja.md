```
add(b1::CompositeGTBasisFuncs{T, D, <:Any, 1}, 
    b2::CompositeGTBasisFuncs{T, D, <:Any, 1}; 
    roundAtol::Real=getAtolVal(T)) where {T, D} -> 
CompositeGTBasisFuncs{T, D, <:Any, 1}
```

`CompositeGTBasisFuncs{T, D, <:Any, 1}`同士の加算は、[`BasisFunc`](@ref) と [`BasisFuncMix`](@ref) のように行われます。`roundAtol`は、各`CompositeGTBasisFuncs`に格納されたパラメータを比較して「等しい」と見なすかどうかを決定するための絶対近似許容誤差を指定します。返される`CompositeGTBasisFuncs`の各パラメータは、`0.5atol`の最も近い正確な倍数に設定されます。`roundAtol`が`NaN`に設定されている場合、近似や丸めは行われません。この関数は、キーワード引数をデフォルト値に設定して`+`構文を使用して呼び出すことができます。

**注意:** 入力引数に格納されている`ParamBox`で、微分不可能としてマークされているものは、可能であれば融合され、新しい`ParamBox`(s)が生成され、もはやそれらに格納されている入力変数にリンクされなくなります。

≡≡≡ 例 ≡≡≡

```jldoctest; setup = :(push!(LOAD_PATH, "../../src/"); using Quiqbox)
julia> bf1 = genBasisFunc([1.,1.,1.], (2.,1.));

julia> bf2 = genBasisFunc([1.,1.,1.], (2.,2.));

julia> bf3 = bf1 + bf2;

julia> bf3.gauss[1].con() == bf1.gauss[1].con() + bf2.gauss[1].con()
true
```
