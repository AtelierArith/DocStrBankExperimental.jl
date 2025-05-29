```
struct FunctionModel{O} <: LeafModel{O}
    f::FunctionWrapper{O}
    info::NamedTuple
end
```

`FunctionModel`は、結果を計算するためにネイティブなJulia `Function`を適用する`LeafModel`です。

!!! warning
    効率の懸念から、`Function`を型`FunctionWrapper{O}`のオブジェクトにラップして出力型`O`を明示的にすることが必須です（[FunctionWrappers](https://github.com/yuyichao/FunctionWrappers.jl)を参照してください）。


また[`LeafModel`](@ref)も参照してください。
