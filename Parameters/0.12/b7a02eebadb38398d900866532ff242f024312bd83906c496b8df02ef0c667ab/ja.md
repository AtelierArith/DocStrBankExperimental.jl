これは数値モデルのパラメータを扱うために使用するパッケージであり、その名前の由来です。しかし、他の用途にも役立つはずです。主に2つの機能があります：

  * デフォルト値を持つキーワード型コンストラクタ、および
  * 複合型や辞書のアンパックとパック。

デフォルト値とキーワードコンストラクタを許可するために型定義を装飾するマクロ `@with_kw`：

```
julia> using Parameters

julia> @with_kw struct A
           a::Int = 6
           b::Float64 = -1.1
           c::UInt8
       end

julia> A(c=4)
A
  a: 6
  b: -1.1
  c: 4
```

アンパックは `@unpack` を使用して行われます（`@pack!` は似ています）：

```
struct B
    a
    b
    c
end
@unpack a, c = B(4,5,6)
# は次のように等価です
BB = B(4,5,6)
a = BB.a
c = BB.c
```
