```
Layout <: MultiGridRenderer

Layout(layout::Array, renderer::Matrix)
```

Layoutは、レイアウト行列と各グリッドに対して実行される[`Image`](@ref)のリストを指定することによって、ブロックレイアウトで複数のグリッドを表示することを可能にします。

# 引数

  * `layout`: 表示する位置にあるグリッドのキーまたは番号を含む`Vector`または`Matrix`。`nothing`、`missing`、または`0`の値はスキップされます。
  * `renderers`: `layout`に一致する[`Image`](@ref)の`Vector/Matrix`。レイアウトにないグリッドには`nothing`または他の任意の値を使用できます。
