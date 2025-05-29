```
@envelope(arguments...)
```

エンベロープを作成します。最初に開始振幅（0から1の間の数値）を指定します。次に、`segment_function` => `duration` のペアを指定します。ここで、`duration` はセグメントの持続時間です。次に、終了振幅（再び0から1の間の数値）を指定します。例えば、

例えば、`@envelope(0, Line => 1s, 1)` は1つのセグメントを持つエンベロープを作成します。セグメントは `segment_function(start_level, duration, end_level) => duration` で作成されます。したがって、この例では、セグメントは `Line(0, 1s, 1) => 1s` になります。

最初のセグメントが終了したら、好きなだけセグメントを追加できます。前のセグメントの終了レベルは、次のセグメントの開始レベルになります。

例えば、`@envelope(0, Line => 1s, 1, Line => 1s, 0)` は2つのセグメントを持つエンベロープを作成します：

1. `Line(0, 1s, 1) => 1s`
2. `Line(1, 1s, 0) => 1s`

```jldoctest
julia> using AudioSchedules

julia> @envelope(0, Line => 1s, 1, Line => 1s, 0)
(Line(0.0, 1.0 s⁻¹) => 1.0 s, Line(1.0, -1.0 s⁻¹) => 1.0 s)

julia> @envelope(1, 2, 3)
ERROR: LoadError: ArgumentError: 2 is not a pair
[...]
```
