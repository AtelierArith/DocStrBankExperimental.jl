```
SeisDelay(in; <キーワード引数>)
```

2Dデータに時間遅延を適用します

# 引数

  * `in`: txドメインの入力2Dデータ配列。最初の次元は時間です。

# キーワード引数

  * `delay=0.1`: 希望する時間遅延（秒単位）。
  * `dt=0.004`: 時間サンプリング間隔（秒単位）。

# 例

```julia
julia> d = SeisLinearEvents(); deli = SeisDelay(d);
```

*クレジット: Aaron Stanton,2017*
