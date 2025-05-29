```
RoundInward = SpanRoundingMode(RoundUp, RoundDown)
```

これは、連続時間間隔の両端が「内側」に丸められ、すべてのサンプルが時間の瞬間としてその間隔内に存在するように、最大のインデックスのスパンを構築する丸めモードです。

## 例

サンプルレートが1 Hzの信号を考えます。

```
Index       1   2   3   4   5
Time (s)    0   1   2   3   4
```

次に、時間スパン1.5秒（含む）から2.5秒（除外）を考えます。このスパンを強調するために括弧を使用します：

```
Index       1   2     3     4   5
Time (s)    0   1  [  2  )  3   4
```

コードでは、このスパンは次のように記述されます。

```jldoctest RoundInward
julia> using AlignedSpans, Dates, TimeSpans

julia> ts = TimeSpan(Millisecond(1500), Millisecond(2500))
TimeSpan(00:00:01.500000000, 00:00:02.500000000)
```

スパン内の唯一のサンプルはインデックス3にあります。そして実際に、

```jldoctest RoundInward
julia> aligned = AlignedSpan(1, ts, RoundInward)
AlignedSpan(1.0, 3, 3)

julia> AlignedSpans.indices(aligned)
3:3
```

はインデックス `3:3` を持つ `AlignedSpan` を返します。
