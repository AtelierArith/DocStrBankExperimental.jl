```
Show(mime::MIME, data)
```

`mime` MIMEタイプとしてレンダリングできるオブジェクトで、`data`をIOストリームに書き込みます。リッチ出力サポートのある環境で使用します。 [`Base.show`](@ref)について詳しく読む。

# 例

```julia
Show(MIME"text/html"(), "私は<b>レンダリング</b>されることができます<em>HTML</em>として！")
```

```julia
Show(MIME"image/png"(), read("dog.png"))
```

`Base.showable`と`Base.show`は`Show`に対して定義されています。

```julia
s = Show(MIME"text/latex"(), "\\frac{hello}{world}")

showable(MIME"text/latex"(), s) == true

repr(MIME"text/latex"(), s) == "\\frac{hello}{world}"
```
