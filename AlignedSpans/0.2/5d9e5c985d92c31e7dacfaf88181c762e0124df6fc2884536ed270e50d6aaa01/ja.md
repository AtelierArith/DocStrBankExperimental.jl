```
RoundSpanDown = SpanRoundingMode(RoundDown, RoundDown)
```

これは、連続時間間隔の*両方*の端が下方向に丸められる丸めモードです。

## 例

サンプルレートが1 Hzの信号を考えます。

```
Index       1   2   3   4   5
Time (s)    0   1   2   3   4
```

次に、時間スパン1.5s（含む）から2.5s（除外）を考えます。このスパンを強調するために括弧を使用します：

```
Index       1   2     3     4   5
Time (s)    0   1  [  2  )  3   4
```

コードでは、このスパンは次のように記述されます。

```jldoctest RoundSpanDown
julia> using AlignedSpans, Dates, TimeSpans

julia> ts = TimeSpan(Millisecond(1500), Millisecond(2500))
TimeSpan(00:00:01.500000000, 00:00:02.500000000)
```

間隔の両端を最寄りのサンプルに下方向に丸めると、間隔の開始は1sになり、間隔の終了は2sになります。したがって、関連するサンプルはインデックス`2:3`にあります。そして実際に、

```jldoctest RoundSpanDown
julia> aligned = AlignedSpan(1, ts, RoundSpanDown)
AlignedSpan(1.0, 2, 3)

julia> AlignedSpans.indices(aligned)
2:3
```

はインデックス`2:3`を持つ`AlignedSpan`を返します。
