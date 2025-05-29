```
make_tokenizer(
    tokens::Union{
        AbstractVector{RE},
        Tuple{E, AbstractVector{Pair{E, RE}}}
    };
    goto::Bool=true,
    version::Int=1,
    unambiguous=false
) where E
```

`TokenizerMachine`をコンパイルし、その後に`make_tokenizer`を実行するための便利な関数です。言い換えれば、この関数は実行されると`Tokenizer{$E, D, $version} where D`の`iterate`を定義するコードを返します。

`tokens`がタプルの場合、最初の要素はエラー・トークンで、次の要素は`token => regex`ペアのベクターです。`tokens`が`AbstractVector{RE}`の`v`である場合、トークンはデフォルトで`UInt32`になり、`(UInt32(0), [UInt32(i)=>r for (i,r) in pairs(v)])`のように振る舞います。すなわち、`UInt32(0)`がエラー・トークンです。

# 例

```jldoctest
julia> make_tokenizer([re"abc", re"def"]) |> eval

julia> collect(tokenize(UInt32, "abcxyzdef123"))
4-element Vector{Tuple{Int64, Int32, UInt32}}:
 (1, 3, 0x00000001)
 (4, 3, 0x00000000)
 (7, 3, 0x00000002)
 (10, 3, 0x00000000)

julia> make_tokenizer((0, collect(pairs([re"x", re"y"]))); version=5) |> eval

julia> iter = tokenize(Int, "xyaby", 5)
Tokenizer{Int64, String, 5}("xyaby")

julia> collect(iter)
4-element Vector{Tuple{Int64, Int32, Int64}}:
 (1, 1, 1)
 (2, 1, 2)
 (3, 2, 0)
 (5, 1, 2)
```
