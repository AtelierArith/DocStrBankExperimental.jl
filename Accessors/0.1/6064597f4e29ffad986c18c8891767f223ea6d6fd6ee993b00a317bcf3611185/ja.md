```
@optic expr
@o expr
```

プロパティ/インデックスアクセス、関数呼び出しなどを含む式からオプティックを構築します。

マクロ内では、`_` はターゲットオブジェクトを参照するためのプレースホルダーとして使用されます。

`@optic` と `@o` の2つの形式は同等です。混乱の可能性がない限り、簡潔さのために `@o` を使用することをお勧めします。

# 例

```jldoctest
julia> using Accessors

julia> struct T;a;b;end

julia> t = T("A1", T(T("A3", "B3"), "B2"))
T("A1", T(T("A3", "B3"), "B2"))

julia> l = @optic _.b.a.b
(@o _.b.a.b)

julia> l(t)
"B3"

julia> set(t, l, 100)
T("A1", T(T("A3", 100), "B2"))

julia> t = ("one", "two")
("one", "two")

julia> set(t, (@o _[1]), "1")
("1", "two")

julia> l = @o _[∗].a
(@o _[∗].a)

julia> modify(x -> x + 1, ((a=1,), (a=2,)), l)
((a = 2,), (a = 3,))
```

[`@set`](@ref) も参照してください。
