```
@rule LHS => RHS
```

`Rule`オブジェクトを作成します。ルールオブジェクトは呼び出し可能で、式を受け取り、LHSパターンに一致する場合はそれをRHSパターンに書き換え、そうでない場合は`nothing`を返します。ルール言語は以下に説明されています。

LHSは、引数のいずれかがオプションでスロット（`~x`）またはセグメント（`~~x`）である可能性のある、任意にネストされた関数呼び出し式であることができます（以下に説明）。

式がLHSに完全に一致する場合、それはRHSのセグメント（`~x`）およびスロット変数（`~~x`）のパターンに書き換えられ、LHSで見つかったこれらの変数の一致の結果が置き換えられます。

**スロット**:

スロット変数は`~x`として書かれ、単一の式に一致します。`x`は変数の名前です。スロットがLHS式に複数回現れる場合、すべてのその位置で一致した式は等しくなければなりません（`isequal`によって示されるように）。

*例:*

任意の`sin`を`cos`に変換する単純なルール：

```julia
julia> @syms a b c
(a, b, c)

julia> r = @rule sin(~x) => cos(~x)
sin(~x) => cos(~x)

julia> r(sin(1+a))
cos((1 + a))
```

2つのセグメント変数を持つルール

```julia
julia> r = @rule sin(~x + ~y) => sin(~x)*cos(~y) + cos(~x)*sin(~y)
sin(~x + ~y) => sin(~x) * cos(~y) + cos(~x) * sin(~y)

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

セグメント変数は`~~x`として書かれ、関数呼び出しの中で0個以上の式に一致します。

*例:*

これは乗法の分配法則を実装します：`+(~~ys)`は`a + b`、`a+b+c`などの式に一致します。RHSでは`~~ys`は古いjulia配列として表現されます。

```julia
julia> r = @rule ~x * +((~~ys)) => sum(map(y-> ~x * y, ~~ys));

julia> r(2 * (a+b+c))
((2 * a) + (2 * b) + (2 * c))
```

**述語**:

述語には2種類あり、スロット変数に対するものと全体のルールに対するものです。前者の場合、述語は`~x`および`~~x`の両方で使用でき、`~x::f`または`~~x::f`を使用します。ここで`f`は任意のjulia関数です。スロットの場合、関数は単一の一致した部分式を受け取り、セグメントの場合は一致した式の配列を受け取ります。

述語は、現在の一致が受け入れ可能であれば`true`を、そうでなければ`false`を返す必要があります。

```julia
julia> two_πs(x::Number) = abs(round(x/(2π)) - x/(2π)) < 10^-9
two_πs (generic function with 1 method)

julia> two_πs(x) = false
two_πs (generic function with 2 methods)

julia> r = @rule sin(~~x + ~y::two_πs + ~~z) => sin(+(~~x..., ~~z...))
sin(~(~x) + ~(y::two_πs) + ~(~z)) => sin(+(~(~x)..., ~(~z)...))

julia> r(sin(a+3π))

julia> r(sin(a+6π))
sin(a)

julia> r(sin(a+6π+c))
sin((a + c))
```

述語関数は、セグメント変数（`~~x`）に付随している場合、値の配列を取得します。

全体のルールに対する述語の場合は、`@rule <LHS> => <RHS> where <predicate>`を使用します：

```
julia> @syms a b;

julia> predicate(x) = x === a;

julia> r = @rule ~x => ~x where f(~x);

julia> r(a)
a

julia> r(b) === nothing
true
```

これは構文的な糖衣構文であり、`@rule ~x => f(~x) ? ~x : nothing`のようなものと同じです。

**コンテキスト**:

*述語内で*: コンテキスト述語は、`Contextual`型でラップされた関数です。この関数は2つの引数（式とルールオブジェクトへの呼び出し中に渡されるコンテキストオブジェクト）で呼び出されます（おそらく`simplify`や`RuleSet`オブジェクトにコンテキストを渡すことによって行われます）。

関数は入力を自由に使用でき、述語が成り立つかどうかを示すブール値を返す必要があります。

*結果パターン内で*: 式の右側でコンテキストオブジェクトにアクセスするには`(@ctx)`を使用します。
