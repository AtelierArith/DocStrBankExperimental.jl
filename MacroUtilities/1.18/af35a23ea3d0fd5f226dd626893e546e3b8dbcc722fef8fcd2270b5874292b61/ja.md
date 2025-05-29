```
@parse_kwargs [args] kwarg_spec
```

`args` に与えられたキーワード式のセットを `kwarg_spec` の一連の仕様に従って解析し、呼び出しスコープ内の対応するキーを設定します。キーワード引数として解析されなかった式の `Vector` を返します。

`kwarg_spec` はブロック `Expr` でなければならず、各行は次の形式の式で構成されます。

```julia
    key = (expected_type = T)
```

これは、`args` 内の `key = value` という形式のキー-バリュー式に対して、`value` が型 `T` でなければならないことを指定します。

代替の形式は次の通りです。

```julia
    key = (expected_types = (T1, T2, ..., Tn))
```

これは、`args` 内の `key = value` というキー-バリュー式が `typeof(value) in (T1, T2, ..., Tn)` でなければならないことを指定します。

`default` キーが提供されている場合、例えば、

```julia
    key = (expected_types = (T1, T2, ..., Tn), default=default_value)
```

この場合、`args` に `key = value` の式が含まれていない場合、`key` は `default_value` に設定されます。

`default` キーが提供されていない場合、`args` には `key = value` の式が含まれていなければならず、そうでない場合は `ArgumentError` がスローされます。

上記の式に対する代替の、よりコンパクトな形式は次の通りです。

```julia
    key::Union{T1, T2, ..., Tn} = default_value
```

注意: `kwarg_spec` の一部として `key::Symbol` が提供されている場合、`args` 内の式 `key` は `key=key)` として扱われます（すなわち、通常のキーワード引数構文 `f(; key)` に似ています）。

# 例

```jldoctest
julia> macro a(args...)
       @parse_kwargs args... begin
           a1::Union{Int, Symbol, Expr}
           a2::Union{String, Nothing}
           a3::Bool = false
       end
       quote
        b1 = $a1
        b2 = $a2
        b3 = $a3
        (; b1, b2, b3)
       end |> esc
       end
@a (macro with 1 method)

julia> let 
           a1 = 1
           @a a1 a2="b2"
       end
(b1 = 1, b2 = "b2", b3 = false)

julia> let 
           @a a2="b2"
       end
ERROR: LoadError: ArgumentError: No value provided for key `a1`
[...]
```
