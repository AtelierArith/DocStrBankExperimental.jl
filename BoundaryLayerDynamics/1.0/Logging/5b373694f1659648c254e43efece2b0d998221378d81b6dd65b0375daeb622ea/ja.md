```
StepTimer(; kwargs...)
```

$$
N
$$

ステップごとにタイムスタンプを収集して、各タイムステップの計算時間を測定し、それを [JSON](https://en.wikipedia.org/wiki/JSON) ファイルに書き込みます。

# キーワード

  * `path = "output/timestamps.json"`: 出力ファイルへのパス。
  * `frequency = 1`: 収集された各タイムスタンプの間に計算されるタイムステップの数 $N$。
