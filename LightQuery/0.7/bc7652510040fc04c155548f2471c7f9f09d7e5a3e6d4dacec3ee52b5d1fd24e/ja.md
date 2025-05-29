```
Name(name)
```

型付き `Name` を作成します。 [`unname`](@ref) の逆です。 [`@name_str`](@ref) も参照してください。

```jldoctest name
julia> using LightQuery


julia> Name(:a)
name"a"
```

`Name` はセレクタ関数として使用できます。

```jldoctest name
julia> using Test: @inferred


julia> data = (a = 1, b = 1.0, c = 1, d = 1.0, e = 1, f = 1.0)
(a = 1, b = 1.0, c = 1, d = 1.0, e = 1, f = 1.0)

julia> @inferred name"c"(data)
1
```

複数の名前をセレクタ関数として使用できます。

```jldoctest name
julia> @inferred (name"c", name"f")(data)
(c = 1, f = 1.0)
```

名前の最終的な使用法は、ペアから NamedTuples を構築する方法としてです。 `Symbol` の代わりに `Name` を使用すると、型の安定性が得られます。

```jldoctest name
julia> @inferred NamedTuple((name"a", 1), (name"b", 2))
(a = 1, b = 2)
```
