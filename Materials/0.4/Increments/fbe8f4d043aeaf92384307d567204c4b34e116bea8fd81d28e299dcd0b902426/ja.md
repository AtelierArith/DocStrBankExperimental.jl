```
stress_driven_general_increment!(material::AbstractMaterial,
                                 dstress_knowns::AbstractVector{<:Union{T, Missing}},
                                 dt::Real,
                                 dstrain::AbstractVector{T},
                                 max_iter::Integer=50, norm_acc::T=1e-9) where T <: Real
```

`material`に対して互換性のあるひずみ増分を見つけます。

材料の状態（`material.variables`）と*応力*増分`dstress_knowns`の非`missing`成分は、指定されたものとして扱われます。

このルーチンは、新しい応力状態のうち、非`missing`成分の`dstress_knowns`に対応する成分が、`material.variables.stress + dstress_knowns`の成分と一致するような*ひずみ*増分を計算します。

`dstress_knowns`の`missing`成分については、新しい応力状態が`material.variables.stress`の対応する成分と一致します。（したがって、`missing`成分はゼロであるかのように振る舞います。）

*すべての*ひずみ増分成分が解かれます。いくつかの成分を指定しながら応力も指定する必要がある場合は、`general_mixed_increment!`を参照してください。

「新しい」応力状態とは、材料を長さ`dt`の1タイムステップで統合した後の応力状態を意味します。

`dstrain`はひずみ増分の初期推測です。

`find_dstrain!`を参照してください。
