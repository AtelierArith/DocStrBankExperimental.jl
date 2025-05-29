```
レンズ
```

`Lens`は、複雑なオブジェクトの深くネストされた部分にアクセスしたり、置き換えたりすることを可能にします。

# 例

```jldoctest
julia> using Setfield

julia> struct T;a;b; end

julia> obj = T("AA", "BB")
T("AA", "BB")

julia> lens = @lens _.a
(@lens _.a)

julia> get(obj, lens)
"AA"

julia> set(obj, lens, 2)
T(2, "BB")

julia> obj
T("AA", "BB")

julia> modify(lowercase, obj, lens)
T("aa", "BB")
```

# インターフェース

`Lens`の具体的なサブタイプは、以下を実装する必要があります。

  * `set(obj, lens, val)`
  * `get(obj, lens)`

これらは純粋な関数であり、3つのレンズの法則を満たさなければなりません。

```jldoctest; output = false, setup = :(using Setfield; (≅ = (==)); obj = (a="A", b="B"); lens = @lens _.a; val = 2; val1 = 10; val2 = 20)
@assert get(set(obj, lens, val), lens) ≅ val
        # 設定したものが得られます。
@assert set(obj, lens, get(obj, lens)) ≅ obj
        # 既にそこにあったものを設定しても何も変わりません。
@assert set(set(obj, lens, val1), lens, val2) ≅ set(obj, lens, val2)
        # 最後に設定したものが勝ちます。

# 出力

```

ここで`≅`は、等価性またはその近似の適切な概念です。ほとんどの文脈では、これは単に`==`です。しかし、いくつかの文脈では、`===`、`≈`、`isequal`または他の何かである可能性があります。例えば、`==`は`Float64`の文脈では機能しません。なぜなら、`get(set(obj, lens, NaN), lens) == NaN`は決して成り立たないからです。代わりに、`isequal`や`≅(x::Float64, y::Float64) = isequal(x,y) | x ≈ y`が可能な代替手段です。

[`@lens`](@ref)、[`set`](@ref)、[`get`](@ref)、[`modify`](@ref)も参照してください。
