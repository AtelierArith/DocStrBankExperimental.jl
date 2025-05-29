```
FieldDict{V}(x) <: AbstractDict{Symbol,V}
```

`x`をラップし、辞書インターフェースを通じてそのフィールドにアクセスを提供します。結果として得られるキーと値のペアは、`x`のフィールド名とそれに対応する値に対応します。

# 例

```jldoctest fielddict_docstring
julia> using FieldDicts

julia> mutable struct Foo
           x::Int
           y::Float64
       end

julia> x = Foo(1, 2);

julia> d = FieldDict(x)
FieldDict{Real, Foo} with 2 entries:
  :x => 1
  :y => 2.0

```

キーとプロパティは、基盤となる構造体のフィールド名と同じです。

```jldoctest fielddict_docstring
julia> keys(d) == propertynames(d) == (:x, :y)
true

```

値も同様に辞書インターフェースを通じてアクセス可能です。

```jldoctest fielddict_docstring
julia> collect(values(d)) == [1, 2]
true

```

これらのフィールドには、従来の辞書のようなアクセスまたはドットプロパティ表記を使用してアクセスできます。

```jldoctest fielddict_docstring
julia> d[:x] = 1;

julia> d.x == d[:x] == 1
true

julia> get(d, :y, 3)
2.0

julia> get(d, :z, 3)
3

```
