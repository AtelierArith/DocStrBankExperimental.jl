```
string_search(str::AbstractString, r::Regex) -> Vector{Tuple{Int, Int}}
```

文字列 `str` の中で正規表現 `r` のパターンを検索します。結果は、マッチの開始位置とその長さを持つ `Tuple{Int, Int}` のベクターになります。両方の値は印刷可能な文字の幅に関連しています。
