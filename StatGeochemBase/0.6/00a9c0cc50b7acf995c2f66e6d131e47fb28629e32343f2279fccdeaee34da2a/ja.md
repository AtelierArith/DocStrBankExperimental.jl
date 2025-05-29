```julia
containsi(haystack, needle)
```

`haystack`と`needle`の両方を文字列に変換し、`string(haystack)`が`string(needle)`を含むかどうかを、大文字と小文字を無視してチェックします。

### 例

```julia
julia> containsi("QuickBrownFox", "brown")
true
```
