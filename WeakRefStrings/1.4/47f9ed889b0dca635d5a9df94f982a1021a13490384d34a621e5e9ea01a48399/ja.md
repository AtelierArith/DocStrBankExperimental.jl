`StringArray{T,N}`

N次元の文字列配列の効率的なストレージ。

`StringArray`は、配列のすべての要素の基になる文字列データを単一の連続バッファに格納します。各要素のオフセットと長さを維持します。

`T`は`String`、`WeakRefString`、`EscapedString`、`Union{Missing, String}`、`Union{Missing, WeakRefString}`、または`Union{Missing, EscapedString}`のいずれかです。`getindex`はこの型を返しますが、`EscapedString`はエスケープされていない`String`を返します。

データをコピーせずに要素の型を変更するには、`convert(StringArray{U}, ::StringArray{T})`を使用して、効率のために`WeakRefString`に変更できます。

# 例の構築

```
julia> sa = StringArray(["x", "y"]) # from Array{String}
2-element WeakRefStrings.StringArray{String,1}:
 "x"
 "y"

julia> sa = StringArray{WeakRefString}(["x", "y"])
2-element WeakRefStrings.StringArray{WeakRefStrings.WeakRefString,1}:
 "x"
 "y"

julia> sa = StringArray{Union{Missing, String}}(["x", "y"]) # with Missing
2-element WeakRefStrings.StringArray{Union{Missing, String},1}:
 "x"
 "y"

julia> sa = StringArray{Union{Missing, String}}(2,2) # undef
2×2 WeakRefStrings.StringArray{Union{Missing, String},2}:
 #undef  #undef
 #undef  #undef
```
