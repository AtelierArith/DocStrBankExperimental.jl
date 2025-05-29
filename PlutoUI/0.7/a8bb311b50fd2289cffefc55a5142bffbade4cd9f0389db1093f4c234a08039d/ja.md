```
Resource(src::String, mime=mime_from_filename(src)[, html_attributes::Pair...])
```

リッチIDEで正しく表示されるURLアドレス付きリソースのコンテナです。

# 例

```
Resource("https://julialang.org/assets/infra/logo.svg")
```

```
Resource("https://interactive-examples.mdn.mozilla.net/media/examples/flower.webm", :width => 100)
```

```
md"""
これはアヒルの鳴き声です: $(Resource("https://interactive-examples.mdn.mozilla.net/media/examples/t-rex-roar.mp3"))
md"""
```
