```
iterdates(time_of_day::Time=Time(0), tz::TimeZone=tz"UTC", occurrence=1)
```

`tz`のタイムゾーンで`time_of_day`に正確に1日1回ティックするノードを作成します。

これはUTCの真夜中にデフォルト設定されています。`tz`が別の値に設定されている場合、各ノットはそのタイムゾーンの`time_of_day`で表示されます。

注意点:     * `TimeDag`内のすべてのノット時間はUTCであると見なされます。     * 毎日存在しない`time_of_day`を選択することが可能です。これにより、評価中に例外が発生します。

特定のノットでは、各値は`DateTime`型であり、ノットの時間と等しくなります。
