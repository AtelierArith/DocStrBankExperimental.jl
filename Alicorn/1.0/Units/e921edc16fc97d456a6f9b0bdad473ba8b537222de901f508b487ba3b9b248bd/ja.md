```
Unit <: AbstractUnit
```

複合単位は、いくつかの [`UnitFactor`](@ref) オブジェクトによって構成されます。

# フィールド

  * `unitFactors::Vector{UnitFactor}`: 乗算（連結）を通じて `Unit` を形成する [`UnitFactor`](@ref) オブジェクトの順序付きリスト。

# コンストラクタ

```
Unit(unitFactors::Vector{UnitFactor})
Unit(abstractUnit::AbstractUnit)
Unit()
```

# 備考

コンストラクタ `Unit(abstractUnit::AbstractUnit)` は [`convertToUnit(abstractUnit::AbstractUnit)`](@ref) と同等です。コンストラクタ `Unit()` は定数 [`unitlessUnit`](@ref) を返します。

`Unit` が初期化されると、`UnitFactor` オブジェクトは出現順に `unitFactors` フィールドに追加されます。同じ基底（`UnitPrefix` と `BaseUnit`）を持つ `UnitFactor` オブジェクトはマージされます。

# 例

1. 単位 $\sqrt{\mathrm{Hz}}/\mathrm{nm}$（ナノメートルあたりのヘルツの平方根）は、次のようにコンストラクタメソッドを使用して構築できます：

    ```jldoctest  julia> ucat = UnitCatalogue();

    julia> sqrtHz = UnitFactor(ucat.hertz, 1/2)  UnitFactor Hz^5e-1

    julia> per_nm = UnitFactor(ucat.nano, ucat.meter, -1)  UnitFactor nm^-1

    julia> sqrtHz*per*nm = Unit([sqrtHz, per_nm])  Unit Hz^5e-1 nm^-1  ```
2. あるいは、$\sqrt{\mathrm{Hz}}/\mathrm{nm}$ は算術的に次のようにも構築できます：

    ```jldoctest  julia> ucat = UnitCatalogue();

    julia> sqrtHz*per*nm = sqrt(ucat.hertz) / ( ucat.nano * ucat.meter )  Unit Hz^5e-1 nm^-1  ```
