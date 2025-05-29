```
split_by_season(var::OutputVar)
```

季節ごとに分割された4つの`OutputVar`のベクトルを返します。

季節の月は、3月から5月（MAM）、6月から8月（JJA）、9月から11月（SON）、12月から2月（JDF）です。ベクトルの順序はMAM、JJA、SON、DJFです。季節に対して日付が見つからない場合、その季節の`OutputVar`は空の`OutputVar`になります。空でない`OutputVar`の場合、季節は`var.attributes["season"]`で見つけることができます。

この関数は、`var.attributes["start_date"]`の開始日を使用します。時間の単位は秒であると期待されています。

!!! note "季節間の補間"
    補間は、返された`OutputVar`のそれぞれの季節の外側の時間間隔では不正確になります。たとえば、`OutputVar`に2010-2-1、2010-3-1、2010-4-1、2011-2-1の日付があり、季節ごとに分割された場合、2010-4-1と2011-2-1の間の時間での補間は不正確になります。


この関数は、`split_by_season_across_time`とは異なり、`split_by_season_across_time`は各年ごとに季節で日付を分割します。
