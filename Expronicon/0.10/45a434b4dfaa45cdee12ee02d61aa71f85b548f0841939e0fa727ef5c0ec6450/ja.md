```
has_plain_constructor(def, name = struct_name_plain(def))
```

構造体定義が `name` のプレーンコンストラクタを含んでいるか確認します。デフォルトでは、名前は推論可能な名前 [`struct_name_plain`](@ref) です。

# 例

```julia
def = @expr JLKwStruct struct Foo{T, N}
    x::Int
    y::N

    Foo{T, N}(x, y) where {T, N} = new{T, N}(x, y)
end

has_plain_constructor(def) # true

def = @expr JLKwStruct struct Foo{T, N}
    x::T
    y::N

    Foo(x, y) = new{typeof(x), typeof(y)}(x, y)
end

has_plain_constructor(def) # false
```

引数には型アノテーションがあってはなりません。

```julia
def = @expr JLKwStruct struct Foo{T, N}
    x::T
    y::N

    Foo{T, N}(x::T, y::N) where {T, N} = new{T, N}(x, y)
end

has_plain_constructor(def) # false
```
