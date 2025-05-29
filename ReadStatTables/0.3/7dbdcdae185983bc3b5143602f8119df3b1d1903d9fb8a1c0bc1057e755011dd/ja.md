```
LabeledValue{T, K}
```

型 `T` の値が、型 `K` のキーを持つ値ラベルの辞書に関連付けられています。値 `v` が辞書のキーと等しくない場合 (`==`)、`string(v)` が値ラベルとして取られます。詳細は [`LabeledArray`](@ref) を参照してください。

`LabeledValue` の基になる値には [`unwrap`](@ref) を介してアクセスできます。値ラベルは [`valuelabel`](@ref) を呼び出すか、`convert` を介して `LabeledValue` を `String` に変換することで取得できます。値ラベルの辞書（通常はデータ列に関連付けられています）には [`getvaluelabels`](@ref) を介してアクセスできます。

比較演算子 `==`、`isequal`、`<`、`isless` および `isapprox` は、型 `T` の基になる値を比較し、値ラベルは無視します。値ラベルを比較するには、まず [`valuelabel`](@ref) を使用してラベルを取得してください。

# 例

```jldoctest
julia> lbls = Dict{Int,String}(0=>"a", 1=>"a");

julia> v0 = LabeledValue(0, lbls)
0 => a

julia> v1 = LabeledValue(1, lbls)
1 => a

julia> vm = LabeledValue(missing, lbls)
missing => missing

julia> v0 == v1
false

julia> v1 == 1
true

julia> isnan(v1)
false

julia> isequal(vm, missing)
true

julia> unwrap(v0)
0

julia> valuelabel(v1) == "a"
true

julia> getvaluelabels(v1) === lbls
true
```
