```
μ(
    material::Union{Element, Material, Matter},
    energies::Union{AbstractArray{<:Unitful.Energy}, T},
    a::Type{<:Attenuation} = DefaultAttenuation,
)
```

与えられた材料の線減衰係数を計算します。

この関数の動作は最初の引数の型によって異なります：

  * `Element`: 関数は元素の密度（`e.ρ`）に与えられたエネルギーに対する質量減衰係数（`μᵨ`）を掛け算し、結果を返します。
  * `Material`: 関数は材料の密度（`m.ρ`）に与えられたエネルギーに対する質量減衰係数（`μᵨ`）を掛け算し、結果を返します。
  * `Matter`: 単一のエネルギー値が配列の代わりに与えられた場合、関数はそれを単一要素の配列に変換し、そのエネルギーに対する線減衰係数を計算します。

引数 `a` は適用する減衰のタイプを決定し、デフォルトは `DefaultAttenuation` です。
