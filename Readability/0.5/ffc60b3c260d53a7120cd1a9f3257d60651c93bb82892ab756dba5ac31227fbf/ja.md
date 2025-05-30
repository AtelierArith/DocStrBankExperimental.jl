```
speaking_time(text::String; wpm::Number=183)::Number
```

`text`のスピーキング時間を秒単位で返します。

## 引数

  * `text::String`: 分析するテキスト。
  * `wpm::Number`: 分/分の単語数。

## 返り値

  * `Float64`: 秒単位のスピーキング時間。
