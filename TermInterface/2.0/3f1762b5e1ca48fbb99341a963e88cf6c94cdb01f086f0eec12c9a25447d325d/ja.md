```
iscall(x)
```

`x`が関数呼び出し式である場合、`true`を返します。`true`の場合、`operation(x)`、`arguments(x)`も`x`に対して定義されている必要があります。

`iscall(x)`が`true`である場合、`isexpr(x)`も*必ず*`true`でなければなりません。逆は必ずしも真ではありません。（関数呼び出しは常に式ノードですが、すべての式ツリーが関数呼び出しを表すわけではありません）。

これは、`head(x)`と`children(x)`が定義されている必要があることを意味します。`operation(x)`と`arguments(x)`とともに。

## 例

関数型言語では、すべての式ツリーが関数呼び出しです（例：SymbolicUtils.jl）。ハイブリッド配列と関数型言語があるとしましょう。式`v[i]`に対する`iscall`は`false`であり、式`f(x)`に対する`iscall`は`true`ですが、両方ともネストされた式であり、`isexpr`は両方とも`true`です。

Juliaの`Expr`についても同様です。`Expr(:block, ...)`は*関数呼び出しではなく*、`operation`と`arguments`はありませんが、`head`と`children`はあります。

`head`/`children`と`operation`/`arguments`の区別は、*関数呼び出し操作をそのヘッドとして表さない*言語を扱う際に必要です。主な例は`Expr(:call, :f, :x)`です：これはそれぞれ`head`と`operation`を持ち、`head`は`:call`、`operation`は`:f`です。

SymbolicUtils.jlのような他のシンボリック式言語では、ノードの`head`は`operation`に対応し、`children`は`arguments`に対応することがあります。
