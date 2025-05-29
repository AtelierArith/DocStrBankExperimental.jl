```
split_by_season_across_time(var::OutputVar)
```

`var`を、時系列でソートされた季節を表す`OutputVar`に分割します。各`OutputVar`は単一の季節に対応し、`OutputVar`の順序は季節の日付によって決まります。戻り値の型は`OutputVar`のベクターです。

季節の月は、3月から5月（MAM）、6月から8月（JJA）、9月から11月（SON）、12月から2月（DJF）です。季節に対して日付が見つからない場合、その季節の`OutputVar`は空の`OutputVar`になります。最初の`OutputVar`は空でないことが保証されています。空でない`OutputVar`の場合、季節は`var.attributes["season"]`で見つけることができます。

この関数は、`var.attributes["start_date"]`の開始日を使用します。時間の単位は秒であると期待されています。

この関数は、`split_by_season`とは異なり、`split_by_season`は季節ごとに日付を分割し、季節が異なる年から来る可能性があることを無視します。
