```
@struct_equal_hash T [fields]
```

構造体 `T` の `==`、`isequal`、および `hash` の定義を生成します。

```julia
    function x::T == y::T
    function isequal(x::T, y::T)
    function hash(x::T, h0::UInt)
```

等価性テストは、タプル `fields` で指定された `T` のフィールドに対して短絡論理を使用して適用されます。`fields` のデフォルトは、宣言された順序での `T` のすべてのフィールドです。ハッシュも同様に、型名 `T` と `fields` で指定されたフィールドに対して計算されます。空の構造体も許可されています。

型は `T{P} where P` のような `UnionAll` 型であることができます。この場合、定義は次のようになります。

```julia
    function x::T{P} == y::T{P} where P
    function isequal(x::T{P}, y::T{P}) where P
    function hash(x::T{P}, h0::UInt) where P
```

ここで、`==` と `isequal` のメソッドは、`x` と `y` が同じ型 `T{P}` の場合にのみ適用されます（同じ `P` のため）。パラメトリック型 `T` に対してこれを望まない場合は、単にパラメータなしの形式を使用できます。

`T` に2つのパラメータがある場合、次のように定義されます。

```julia
    @struct_equal_hash T{P,Q} where {P,Q}
```

これは、`==` と `isequal` の2つの引数の型 `P` と `Q` が一致する必要があるメソッドを定義します。最初の型のみが一致することを望む場合は、次のように言えます。

```julia
    @struct_equal_hash T{P,Q where Q} where P
```

または、同等に、

```julia
    @struct_equal_hash T{P} where P
```

2番目の型のみが一致することを望む場合は、次のように言えます。

```julia
    @struct_equal_hash T{P where P,Q} where Q
```

両方の型が異なる可能性がある場合は、次のように言えます。

```julia
    @struct_equal_hash T{P where P,Q where Q}
```

または再びパラメータを省略します。

# 例

```julia
julia> struct T{P}; x::Int; y::P end

julia> @struct_equal_hash T

julia> @struct_equal_hash T{Char} (:x,)

julia> @struct_equal_hash T{P} where P <: Number (:y,)

julia> T(1, "a") == T(1, "b")   # T のメソッド
false

julia> T(1, [1, 2]) == T(1, [1.0, 2.0])   # T のメソッド
true

julia> T(1, 'a') == T(1, 'b')   # T{Char} のメソッド
true

julia> T(1, 1) == T(2, 1)       # T{P} where P <: Number のメソッド
true
```
