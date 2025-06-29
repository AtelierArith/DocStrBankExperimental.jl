```
Cron(second, minute, hour, day_of_month, month, day_of_week)
Cron(;
    second = 0,
    minute = '*',
    hour = '*',
    day_of_month = '*',
    month = '*',
    day_of_week = '*',
)
```

`Cron`は、Linuxベースの`crontab`(5)テーブルに従って実装された繰り返し`Job`のスケジュールを保存します。

ジョブは、**秒、分、時間、月**のフィールドが現在の時間と一致する場合に実行されます。`day_of_month`または`day_of_week`のいずれも**`*`で始まらない**場合、cronはそれらの値の和集合 (∪) `day_of_month ∪ day_of_week`を取ります。そうでない場合、cronはそれらの値の共通集合 (∩) `day_of_month ∩ day_of_week`を取ります。

## 引数が`Int`の場合:

|          フィールド |      許可される値 |
| --------------:| -----------:|
|       `second` |        0-59 |
|       `minute` |        0-59 |
|         `hour` |        0-23 |
| `day_of_month` |        1-31 |
|        `month` |        1-12 |
|  `day_of_week` | 1-7 (1は月曜日) |

!!! compat "Linux crontabとの違い"
    1. 一般的なLinuxディストリビューションには、JobSchedulersとして`second`フィールドがありません。
    2. 日曜日はJobSchedulersでは`7`のみでコード化されていますが、Linuxでは`0`または`7`であるため、`day_of_week = "*/2"`のような動作は2つのシステムで異なります。
    3. JobSchedulers v0.11から、`Cron`は標準のcrontabに基づいて書き直され、[ここ](https://crontab.guru/cron-bug.html)に記載されたバグが含まれています。


## 引数が`String`または`Char`の場合:

引数はアスタリスク（`*`）である場合があり、これは常に$最初-最後$を表します。

数値の範囲が許可されています。範囲はハイフンで区切られた2つの数値です。指定された範囲は包括的です。例えば、8-11の$時間$エントリは、時間8、9、10、11での実行を指定します。

リストが許可されています。リストは、カンマで区切られた数値（または範囲）の集合です。例: `"1,2,5,9"`、`"0-4,8-12"`。

ステップ値は範囲と組み合わせて使用できます。範囲の後に`/<number>`を付けると、その数値の値を通じて範囲をスキップします。例えば、`"0-23/2"`は`hour`引数で使用して、毎時実行を指定できます（代替は`"0,2,4,6,8,10,12,14,16,18,20,22"`です）。アスタリスクの後にもステップが許可されているので、$2時間ごと$と言いたい場合は、`"*/2"`を使用してください。

## 引数が`Vector`の場合:

`Vector`は、上記のリストのように機能します。例えば、`[1,2,5,9]`は`"1,2,5,9"`と同等です。

## 引数が`UInt64`の場合:

`UInt64`は`Cron`フィールドの内部型です。すべての前の型は`UInt64`ビット配列に変換されます。ビット配列の開始インデックスは0です。許可されていない値の外側のビット（上記の表を参照）は無視されます。
