```
operate_to!(output, op::Function, args...)
```

`output`の値を`op(args...)`の値と等しくなるように変更します。`mutability(output, op, args...)`が[`IsMutable`](@ref)を返す場合にのみ呼び出すことができます。

もし`output === args[i]`である`i`が存在する場合、この関数はエラーをスローする可能性があります。その代わりに`operate!!`または`operate!`を使用してください。

例えば、DynamicPolynomialsでは、`operate_to!(p, +, p, q)`はエラーをスローします。なぜなら、そうでなければアルゴリズムは`p`と`q`の項を反復処理しながら`p`を埋めてしまい、決して終了しないからです。一方、`operate!(+, p, q)`は、`q`の項を`p`の項のソートされたリストに最小限の移動で効率的に挿入する異なるアルゴリズムを使用します。
