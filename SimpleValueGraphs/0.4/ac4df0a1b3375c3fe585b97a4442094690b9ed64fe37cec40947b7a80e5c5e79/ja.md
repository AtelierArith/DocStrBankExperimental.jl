```
squash(g::ValGraph)
squash(g::ValDiGraph)
squash(g::ValOutDiGraph)
```

`g`のコピーを返し、`eltype`を可能な限り小さくします。

これによりパフォーマンスが向上する可能性があります。`eltype`のみが変更され、他のすべての型はそのままです。
