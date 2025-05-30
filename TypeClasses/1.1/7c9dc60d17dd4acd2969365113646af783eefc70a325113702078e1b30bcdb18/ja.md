```
combine(::T, ::T)::T  # このオーバーロード
⊕(::T, ::T)::T  # エイリアス \oplus
combine(a, b, c, d, ...)  # 内部で combine(a, b) を使用
```

結合的なコンビネータ演算子。

記号 `⊕` (\oplus) は http://hackage.haskell.org/package/base-unicode-symbols-0.2.3/docs/Data-Monoid-Unicode.html に従う

# 次の法則が成り立つべきである

結合性

```
⊕(::T, ⊕(::T, ::T)) == ⊕(⊕(::T, ::T), ::T)
```
