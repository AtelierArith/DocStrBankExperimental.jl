```
parse_hour_idxs(s::AbstractString) -> comparisons
```

年の比較を解析します。次の形式を取ることができます：

  * `"1"` - 時間1のみ
  * `""` - すべての時間、(:)を返します
  * `"season=>winter"` - "season"=>"winter"を返します
