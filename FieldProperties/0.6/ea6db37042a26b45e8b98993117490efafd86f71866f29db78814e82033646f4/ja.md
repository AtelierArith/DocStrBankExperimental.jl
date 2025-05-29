```
@defprop Property{name}::Type block
```

`getproperty` と `setproperty!` メソッドをラップするプロパティを作成する便利な方法です。

## 例

最も簡単な形は、単にゲッターとセッターを作成します。

```jldoctest defprop
julia> using FieldProperties

julia> @defprop Property1{:prop1}

julia> name(prop1)
:prop1

julia> prop1_type(:any_type)
Any
```

プロパティの型を定義します。

```jldoctest defprop
julia> @defprop Property2{:prop2}::Int

julia> name(prop2)
:prop2

julia> prop2_type(:any_type)
Int64
```

型の要件とデフォルト値を定義します。

```jldoctest defprop
julia> @defprop Property3{:prop3}::Int begin
           @getproperty x -> 1
       end

julia> name(prop3)
:prop3

julia> prop3_type(:any_type)
Int64

julia> prop3(3)
1
```

デフォルト値を定義しますが、強制される戻り型はなく、複数の `getproperty` メソッドがあります。

```jldoctest defprop
julia> @defprop Property4{:prop4} begin
           @getproperty x::Int -> 1
           @getproperty x::String -> "1"
       end

julia> name(prop4)
:prop4

julia> prop4_type(:any_type)
Any

julia> prop4(1)
1
```
