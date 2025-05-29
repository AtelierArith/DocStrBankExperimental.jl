```
split_by_month(var::OutputVar)
```

`var`を月を表す`OutputVar`に分割し、時系列順にソートします。各`OutputVar`は1つの月に対応し、`OutputVar`の順序はその月の日付によって決まります。戻り値の型は`OutputVar`のベクターです。

月に対して日付が見つからない場合、その季節の`OutputVar`は空の`OutputVar`になります。非空の`OutputVar`の場合、月は`var.attributes["month"]`で見つけることができます。

この関数は`var.attributes["start_date"]`の開始日を使用します。時間の単位は秒であると期待されます。
