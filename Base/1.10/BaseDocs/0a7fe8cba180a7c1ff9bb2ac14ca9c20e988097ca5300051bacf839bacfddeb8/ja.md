```
isdefined(m::Module, s::Symbol, [order::Symbol])
isdefined(object, s::Symbol, [order::Symbol])
isdefined(object, index::Int, [order::Symbol])
```

グローバル変数またはオブジェクトフィールドが定義されているかどうかをテストします。引数には、モジュールとシンボル、または複合オブジェクトとフィールド名（シンボルとして）またはインデックスを指定できます。オプションで、操作のための順序を定義できます。フィールドが `@atomic` として宣言されている場合、その仕様はその位置へのストアと互換性があることが強く推奨されます。そうでない場合、`@atomic` として宣言されていない場合は、指定された場合、このパラメータは `:not_atomic` でなければなりません。

配列要素が定義されているかどうかをテストするには、[`isassigned`](@ref) を使用してください。

他にも [`@isdefined`](@ref) を参照してください。

# 例

```jldoctest
julia> isdefined(Base, :sum)
true

julia> isdefined(Base, :NonExistentMethod)
false

julia> a = 1//2;

julia> isdefined(a, 2)
true

julia> isdefined(a, 3)
false

julia> isdefined(a, :num)
true

julia> isdefined(a, :numerator)
false
```
