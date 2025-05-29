```
dynamic(time::Symbol, exc, s::TreatmentSharpness=sharp())
```

引数によって設定されたフィールドを持つ[`DynamicTreatment`](@ref)を構築します。デフォルトでは、`s`は[`SharpDesign`](@ref)に設定されています。`@formula`を使用する際、`dynamic`のラッパーメソッドがこのメソッドを呼び出します。

# 例

```jldoctest; setup = :(using DiffinDiffsBase)
julia> dynamic(:month, -1)
シャープダイナミック治療:
  時間変数の列名: month
  除外された相対時間: -1

julia> typeof(dynamic(:month, -1))
DynamicTreatment{SharpDesign}

julia> dynamic(:month, -3:-1)
シャープダイナミック治療:
  時間変数の列名: month
  除外された相対時間: -3, -2, -1

julia> dynamic(:month, [-2,-1], sharp())
シャープダイナミック治療:
  時間変数の列名: month
  除外された相対時間: -2, -1
```
