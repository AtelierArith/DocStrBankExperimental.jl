```
JD, MJD = datevec2jdate(dateVec; system::Symbol=:UTC)
```

日付ベクターをユリウス日と修正ユリウス日に変換します。

日付ベクターは、[年、月、日、時、分、秒]の浮動小数点数からなる長さ6のベクターです。

`system`キーワード引数は、日付ベクターがどの時間系にあるかを定義します。これは、:UTC（デフォルト）、:UT1、:TAI、:TT、および: TDBから選択できます。

返される値は、通常のSOFA方式で2つの部分に分けて返されるユリウス日です。完全なユリウス日は、ベクターの2つの成分を加えることで単一の数値として得られます。これは`(M)JD.epoch`で見つけることができます。

SOFAの`cal2jd`および`dtf2d`から派生しています。
