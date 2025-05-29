```
UnitPrefix  <: AbstractUnitElement
```

基本単位の前に付けることができるメトリック接頭辞。接頭辞は、単位が対応する係数でスケーリングされていることを示します。

# フィールド

  * `name::String`: 接頭辞の長い形式の名前
  * `symbol::String`: 複合単位で接頭辞を示すために使用される短い記号
  * `value`: 接頭辞の数値

# コンストラクタ

```
UnitPrefix(;name::String, symbol::String, value::Real)
```

文字列 `name` は識別子として有効である必要があります。数値 `value` は有限である必要があります。

# 例外を発生させる条件

  * `Core.ArgumentError`: 有効な識別子としての文字列で `name` フィールドを初期化しようとした場合
  * `Core.DomainError`: 無限大の数で `value` フィールドを初期化しようとした場合

# 例

国際単位系の接頭辞 "milli" は、Alicorn ではデフォルトで次のように定義されています。

```jldoctest
julia> UnitPrefix(name="milli", symbol="m", value=1e-3)
UnitPrefix milli (m) of value 1e-3
```
