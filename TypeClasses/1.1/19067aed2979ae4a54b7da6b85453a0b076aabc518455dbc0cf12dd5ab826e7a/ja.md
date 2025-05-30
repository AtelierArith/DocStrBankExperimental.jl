```
neutral
neutral(::Type)
neutral(_default_return_value) = neutral
```

`⊕`の中立要素、または「単位要素」とも呼ばれます。`neutral`は、具体的な型の中立要素を提供する関数であり、また、すべてと組み合わせることができるシングルトン値として使用することもできます。

デフォルトでは、`neutral(type)`は一般的な`neutral`シングルトンを返します。特定の型に対してより具体的な中立値を持たせるために、これをオーバーライドすることができます。

私たちは、https://en.wikipedia.org/wiki/Identity_element に従って名前を`neutral`と決定しました。代替案は不適切に思えます。

  * "identity"はすでに使用されています
  * "identity_element"は長すぎるようです
  * "I"はあいまいすぎます
  * "unit"は物理単位とあいまいです

## 次の法則が成り立つべきです

左単位

```
  ⊕(neutral(T), t::T) == t
```

右単位

```
  ⊕(t::T, neutral(T)) == t
```
