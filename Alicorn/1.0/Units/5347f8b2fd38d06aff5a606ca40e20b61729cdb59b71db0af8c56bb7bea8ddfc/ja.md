```
BaseUnit <: AbstractUnit
```

七つの基本SI単位から派生した名前付き単位です。

# フィールド

  * `name::String`: 単位の長い形式の名前
  * `symbol::String`: 複合単位で名前付き単位を示すために使用される短い記号
  * `prefactor::Real`: 名前付き単位に対応する基本SI単位の多項式を掛ける数値の前因子。
  * `exponents::BaseUnitExponents`: 名前付き単位に対応する基本SI単位の多項式における指数のコレクション。

# コンストラクタ

```
BaseUnit(; name::String, symbol::String, prefactor::Real, exponents::BaseUnitExponents)
```

# 例外を発生させる

  * `Core.ArgumentError`: 有効な識別子として無効な文字列で`name`フィールドを初期化しようとした場合
  * `Core.DomainError`: 無限大の数値で`prefactor`フィールドを初期化しようとした場合

# 例

1. メートルは次のように表現できます

    `jldoctest  julia> BaseUnit( name="meter",                   symbol="m",                   prefactor=1,                   exponents=BaseUnitExponents(m=1) )  BaseUnit meter (1 m = 1 m)`
2. グラムは次のように表現できます

    `jldoctest  julia> BaseUnit( name="gram",                   symbol="g",                   prefactor=1e-3,                   exponents=BaseUnitExponents(kg=1) )  BaseUnit gram (1 g = 1e-3 kg)`
3. ジュールは次のように定義されます

    `math  1\,\mathrm{J} = 1\,\mathrm{kg}\,\mathrm{m^2}\,\mathrm{s^{-2}}.`

    そして次のように表現できます

    `jldoctest  julia> BaseUnit( name="joule",                   symbol="J",                   prefactor=1,                   exponents=BaseUnitExponents(kg=1, m=2, s=-2) )  BaseUnit joule (1 J = 1 kg m^2 s^-2)`
