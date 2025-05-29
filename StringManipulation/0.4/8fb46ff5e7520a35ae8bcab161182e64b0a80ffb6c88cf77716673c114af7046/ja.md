```
string_search_per_line(str::AbstractString, r::Regex) -> Vector{NTuple{3, Int}}
```

文字列 `str` の各行で正規表現 `r` のパターンを検索します。これは文字列のベクトル `lines` としても渡すことができます。結果は `NTuple{3, Int}` のベクトルで、行、マッチの開始位置、およびその長さを含みます。最後の2つの値は印刷可能な文字の幅に関連しています。
