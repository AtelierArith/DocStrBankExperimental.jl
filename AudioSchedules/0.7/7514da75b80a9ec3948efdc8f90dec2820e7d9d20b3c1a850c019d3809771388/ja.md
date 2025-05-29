```
push!(audio_schedule::AudioSchedule, synthesizer, start_time,
    start_level, shape => duration, end_level, more_segments...
)
```

[`AudioSchedule`](@ref) にシンセサイザーを追加します。ここで `synthesizer` は [`make_series`](@ref) をサポートするものであり、`start_time` は時間の単位（例えば `s`）を持ち、残りの引数はエンベロープの形状を指定します。

すべてのエンベロープ [`segment`](@ref) に対して、次のように呼び出します。

```
segment(shape, start_level, duration, end_level)
```

`duration` は時間の単位（例えば `s`）を持つ必要があります。例えば、

```
push!(audio_schedule, synthesizer, start_time, @envelope(0, Line => 1s, 1, Line => 1s, 0))
```

は次のように segment を2回呼び出します。

```
segment(Line, 0, 1s, 1)
segment(Line, 1, 1s, 0)
```
