```
@Compute(...)
```

`@Compute`マクロは、`NamedTuple`のようなオブジェクトのプロパティに対して計算を行う関数を返します。

入力式は標準のJuliaコードで、プロパティ名の前に`$`が付けられます。たとえば、`a`という名前のプロパティを参照したい場合は、式の中で`$a`を使用します。

# 例

```julia
julia> nt = (a = 1, b = 2.0, c = false)
(a = 1, b = 2.0, c = false)

julia> @Compute($a + $b)(nt)
3.0
```
