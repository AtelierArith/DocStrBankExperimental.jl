```
duration(x)
```

信号の持続時間を秒単位で返します。既知でない場合は `missing` を返すことがあります（例：ストリームの場合）。

!!! note
    `duration` のフォールバック実装は `nframes(x) / framerate(x)` を使用します。ただし、これらのいずれかまたは両方が `missing` の場合、`duration` が非欠損値を返すようにしたい場合は、`duration` のカスタムメソッドを定義できます。

