```
@rule LHS => RHS
```

`Rule`オブジェクトを作成します。ルールオブジェクトは呼び出し可能で、式を受け取り、LHSパターンに一致する場合はそれをRHS式に書き換え、そうでない場合は`nothing`を返します。ルール言語は以下に説明されています。

LHSは、引数のいずれかがオプションでスロット（`~x`）またはセグメント（`~x...`）である可能性のある、任意にネストされた関数呼び出し式であることができます（以下に説明）。

式がLHSに完全に一致する場合、それはスロットの一致を変数として含むRHS式の結果に書き換えられます。

**スロット**:

スロット変数は`~x`として書かれ、単一の式に一致します。`x`は変数の名前です。LHS式にスロットが複数回現れる場合、すべてのその位置で一致した式は等しくなければなりません（`isequal`によって示されるように）。

*例:*

任意の`sin`を`cos`に変換する単純なルール：

```julia
julia> @syms a b c
(a, b, c)

julia> r = @rule sin(~x) => cos(x)
sin(~x) => cos(x)

julia> r(sin(1+a))
cos((1 + a))
```

2つのセグメント変数を持つルール

```julia
julia> r = @rule sin(~x + ~y) => sin(x)*cos(y) + cos(x)*sin(y)
sin(~x + ~y) => sin(x) * cos(y) + cos(x) * sin(y)

julia> r(sin(a + b))
cos(a)*sin(b) + sin(a)*cos(b)
```

同じ式の2つに一致するルール：

```julia
julia> r = @rule sin(~x)^2 + cos(~x)^2 => 1
sin(~x) ^ 2 + cos(~x) ^ 2 => 1

julia> r(sin(2a)^2 + cos(2a)^2)
1

julia> r(sin(2a)^2 + cos(a)^2)
# nothing
```

**セグメント**:

セグメント変数は、関数呼び出し内の0個以上の式に一致します。セグメントはスロット変数をスプラットすることで書くことができます（`~x...`）。

*例:*

これは乗法の分配法則を実装します：`+(~ys...)`は`a + b`、`a+b+c`などの式に一致します。RHSでは`ys`は古いjulia配列として表現されます。

```julia
julia> r = @rule ~x * +((~ys...)) => sum(map(y-> x * y, ys));

julia> r(2 * (a+b+c))
((2 * a) + (2 * b) + (2 * c))
```

**述語**:

述語には、スロット変数に対するものとルール全体に対するものの2種類があります。前者の場合、述語は`~x`および`~x...`の両方で使用でき、`~x::f`や`~x::f...`のように書くことができます。ここで`f`は任意のjulia関数です。スロットの場合、関数は単一の一致した部分式を受け取り、セグメントの場合は一致した式の配列を受け取ります。

述語は、現在の一致が受け入れ可能であれば`true`を、そうでなければ`false`を返す必要があります。

```julia
julia> two_πs(x::Number) = abs(round(x/(2π)) - x/(2π)) < 10^-9
two_πs (generic function with 1 method)

julia> two_πs(x) = false
two_πs (generic function with 2 methods)

julia> r = @rule sin(+(~x..., ~y::two_πs, ~z...)) => sin(+(x..., z...))
sin(+(x..., y::two_πs, z...)) => sin(+(x..., z...))

julia> r(sin(a+3π))

julia> r(sin(a+6π))
sin(a)

julia> r(sin(a+6π+c))
sin((a + c))
```

ルール全体に対する述語の場合は、`@rule <LHS> => <RHS> where <predicate>`を使用します：

```
julia> @syms a b;

julia> predicate(x) = x === a;

julia> r = @rule ~x => x where f(x);

julia> r(a)
a

julia> r(b) === nothing
true
```

これは構文的な糖衣構文であり、`@rule ~x => f(x) ? x : nothing`のようなものと同じです。

**互換性**: セグメント変数は依然として（`~~x`）として書くことができ、RHSのスロット（`~x`）およびセグメント（`~x...`または`~~x`）構文は一致の結果を置き換えます。

参照： [`@capture`](@ref)
