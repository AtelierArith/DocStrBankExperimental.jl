```
lowerbound(distmat)
```

最適なTSPツアーのコストの下限を求めます。現在考慮されている下限は、各都市への出入りの最小コストに基づく単純な下限と、Held-Karp下限に触発されたやや良い下限です。ここでの実装は、適切なHK下限よりも簡単で緩いことに注意してください。

Held-Karpに触発された下限は、多くのスパニングツリーを計算する必要があります。より速いが通常は緩い下限を使用するには、`TravelingSalesmanHeuristics.vertwise_bound(distmat)`を使用してください。

!!! note
    スパニングツリーの下限は対称問題インスタンスでのみ正しく、渡された`distmat`が対称でない場合は使用されません。これらの下限を使用したい場合（例えば、ほぼ対称のインスタンスの場合）は、`TravelingSalesmanHeuristics.hkinspired_bound`を使用してください。

