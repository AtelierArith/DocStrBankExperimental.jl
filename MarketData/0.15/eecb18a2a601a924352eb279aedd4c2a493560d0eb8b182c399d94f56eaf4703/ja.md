```
struct YahooOpt <: AbstractQueryOpt
  period1  # 開始時間
  period2  # 終了時間
  interval # "1d", "1wk" または "1mo"
  events   # 現在は `:history` のみサポート
end
```

Yahoo Finance HTTP API クエリオブジェクト。

# 例

```jl-repl
julia> t = Dates.now()
2020-08-09T01:38:04.735

julia> YahooOpt(period1 = t - Year(2), period2 = t)
YahooOpt{DateTime} with 4 entries:
  :period1  => 1533778685
  :period2  => 1596937085
  :interval => "1d"
  :events   => :history
```
