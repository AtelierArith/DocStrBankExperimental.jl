```
μᵨ(
    material::Union{Matter, Element, Compound, Mixture, Material},
    energies::AbstractArray{<:Unitful.Energy},
    a::Type{A} = DefaultAttenuation,
)
```

与えられた材料の質量減衰係数を計算します。

この関数の動作は最初の引数の型によって異なります：

  * `Matter`: `energies` 配列は単一のエネルギー値に変換されます。
  * `Element`: この関数は元素の原子番号 (`e.Z`) を使用して XCOM サービスのリクエストボディを作成し、与えられたエネルギーに対する質量減衰係数を cm²/g で返します。
  * `Compound`: `Element` と似ていますが、原子番号の代わりに化合物の式を使用します。
  * `Mixture`: この関数は混合物の式の文字列表現を持つリクエストボディを作成し、XCOM サービスを使用して与えられたエネルギーに対する質量減衰係数を計算します。
  * `Material`: この関数は材料の組成を `Mixture` に変換し、その後 `Mixture` の場合と同様に進行します。

引数 `a` は適用する減衰のタイプを決定し、デフォルトは `DefaultAttenuation` です。
