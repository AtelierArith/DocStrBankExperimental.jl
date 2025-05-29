```
@properties T block
```

カスタム `getproperty`、`setproperty!`、および `propertynames` メソッドのための構文糖です。`@properties` に渡された任意の型 `T` に対して、これらのメソッドはデフォルトから書き換えられます。

## 例

以下の構文は、プロパティ名を関数呼び出しに割り当てます。

```jldoctest properties
julia> using FieldProperties

julia> mutable struct MyType
           x::Int
       end

julia> @properties MyType begin
           xint(self) = getfield(self, :x)
           xint!(self, val) = setfield!(self, :x, val)
           hello(self) = "hello"
       end

julia> mt = MyType(1)
MyType(1)

julia> mt.xint
1

julia> mt.xint = 2
2

julia> mt.xint
2

julia> mt.hello
"hello"

julia> propertynames(mt)
(:xint, :hello)

julia> mt.x
ERROR: Property x not found
[...]
```

ここで覚えておくべきことは3つです：

1. `getproperty`、`setproperty!`、および `propertynames` はここで完全に上書きされています。
2. `!` で終わる任意のプロパティ割り当ては `setproperty!` を割り当てるために使用されます。
3. `MyType` はもはや `mt.x` を介して `x` フィールドにアクセスできません（最初のポイントのためです）。

すべての `getfield` と `setfield` メソッドを書くのは少し面倒なので、フィールドを割り当てるために `=>` を使用してこれをやり直しましょう。

```jldoctest properties
julia> @properties MyType begin
           xint(self) => :x
           xint!(self, val) => :x
           hello(self) = "hello"
       end

julia> mt = MyType(1)
MyType(1)

julia> mt.xint
1

julia> mt.xint = 2
2

julia> mt.xint
2

julia> mt.hello
"hello"

julia> propertynames(mt)
(:xint, :hello)

julia> mt.x
ERROR: Property x not found
[...]
```

時には、型を構築するためにモジュラーアプローチを使用したいことがあります。以下の例では、ユーザーが `x1`、`x2`、および `x3` フィールドを見つける場所を知っている必要があります。

```jldoctest properties
julia> mutable struct PropList1
           x2::Int
       end

julia> mutable struct PropList2
           x3::Int
       end

julia> mutable struct MyProperties
           x1::Int
           l1::PropList1
           l2::PropList2
       end

julia> mp = MyProperties(1, PropList1(2), PropList2(3))
MyProperties(1, PropList1(2), PropList2(3))

julia> mp.x1
1

julia> mp.l1.x2  # ユーザーにとって不快
2

julia> mp.l2.x3  # ユーザーにとっても不快
3
```

以下の構文は、プロパティメソッドにネストされたフィールドを検索するように指示します。

```jldoctest properties
julia> @properties MyProperties begin
           x1(self) => :x1
           x1!(self, val) => :x1
           Any(self) => (:l1, :l2)
           Any!(self, val) => (:l1, :l2)
       end

julia> propertynames(mp)
(:x1, :x2, :x3)

julia> mp.x1
1

julia> mp.x2
2

julia> mp.x3
3
```

最後の2つのメソッド（`Any(x)` と `Any!(x, val)`）は、`getproperty` と `setproperty!` メソッドに `l1` と `l2` フィールドを検索して、`:x1` ではない任意のプロパティを探すように指示します。

下記のコードが生成されます：

```julia
julia> @macroexpand @properties MyProperties begin
                  x1(self) => :x1
                  x1!(self, val) => :x1
                  Any(self) => (:l1, :l2)
                  Any!(self, val) => (:l1, :l2)
              end
quote
    function Base.getproperty(self::MyProperties, p::Symbol)
        if p === :x1
            getfield(self, :x1)
        else
            if hasproperty(getfield(self, :l1), p)
                getproperty(getfield(self, :l1), p)
            else
                getproperty(getfield(self, :l2), p)
            end
        end
    end
    function Base.setproperty!(self::MyProperties, p::Symbol, val)
        if p === :x1
            setfield!(self, :x1, val)
        else
            if hasproperty(getfield(self, :l1), p)
                setproperty!(getfield(self, :l1), p, val)
            else
                setproperty!(getfield(self, :l2), p, val)
            end
        end
    end
    function Base.propertynames(self::MyProperties)
        (:x1, propertynames(getfield(self, :l1))..., propertynames(getfield(self, :l2))...)
    end
end
```

`:l1` と `l2` フィールドは、マクロ内で呼び出される順序で検索されることに注意してください（例：`Any(x) => (:l1, :l2)` は `:l1` の後に `:l2` を検索します）。
