```
RoundFullyContainedSampleSpans
```

これは特別な丸めモードで、他の丸めモードとは異なり、各サンプルを*スパン*（サンプルが発生する瞬間から次のサンプルが発生する直前まで）に関連付け、入力スパンに完全に含まれる「サンプルスパン」へ内側に丸めます。

これは、ある意味で[`RoundInward`](@ref)が提供する内側への丸めよりも厳密な形式です。

## 例

サンプルレートが1 Hzの信号を考えます。

```
Index       1   2   3   4   5
Time (s)    0   1   2   3   4
```

通常、各サンプルは時間の瞬間に発生すると考えます。`RoundFullyContainedSampleSpans`では、サンプルが発生する瞬間と次のサンプルの間のスパンを考えます。（これはデジタルセンサーには通常意味がありませんが、サンプルがある時間領域を要約するようなヒプノグラムなどには意味があります）。

したがって、各インデックス（各サンプル）に1秒の閉区間を関連付けます：

```
Index        1     2     3     4     5
Span (s)    [0   )[1   )[2   )[3   )[4    )
```

スパンの持続時間は`1/sample_rate`であり、この例では1秒です。

次に、入力時間スパン1.5秒（含む）から3.5秒（除く）を考えます。このスパンを強調するためにブラケットを使用します：

```
Index        1     2     3     4     5
Span (s)    [0   )[1   )[2   )[3   )[4    )
Time (s)     0     1  [  2     3  )  4
```

この入力スパンには、サンプルスパン`[2s, 3s)`のみが含まれています。`[1s, 2)`のスパンは完全には含まれておらず、`[3s, 4s)`のスパンも同様です。

したがって、このシナリオでは、`RoundFullyContainedSampleSpans`はインデックス3に関連付けられた単一のサンプルを返します。これは`[2s, 3s)`に関連しています。

コードでは、このスパンは次のように記述されます。

```jldoctest RoundFullyContainedSampleSpans
julia> using AlignedSpans, Dates, TimeSpans

julia> ts = TimeSpan(Millisecond(1500), Millisecond(3500))
TimeSpan(00:00:01.500000000, 00:00:03.500000000)

julia> aligned = AlignedSpan(1, ts, RoundFullyContainedSampleSpans)
AlignedSpan(1.0, 3, 3)

julia> AlignedSpans.indices(aligned)
3:3
```
