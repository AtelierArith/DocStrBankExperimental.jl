```
Push(t::Turtle)
```

カメの位置と向きをスタックに保存します。

`Pop()`を使用して、スタックの最上部の値からこの位置と向きを復元し、現在の位置と向きを破棄します。

カメは社交的な生き物であり、スタックは1つだけで、すべてのカメによって共有されています。そのため、1匹のカメが別のカメによって`pushed`されたスタックの値を`pop`することが可能です。
