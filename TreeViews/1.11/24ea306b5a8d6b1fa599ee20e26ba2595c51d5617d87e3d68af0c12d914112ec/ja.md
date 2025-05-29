```
treelabel(io::IO, x, mime = MIME"text/plain"())
```

`x`のツリーヘッダーを`io`に出力します。`Base.show`と同様に、`mime::AbstractString`を持つメソッドや、`mime`引数が全くないメソッドもあります（これは`MIME"text/plain"()`にフォールバックします）。`treelabel(io::IO, x, mime::MIME)`形式のみをオーバーロードしてください。
