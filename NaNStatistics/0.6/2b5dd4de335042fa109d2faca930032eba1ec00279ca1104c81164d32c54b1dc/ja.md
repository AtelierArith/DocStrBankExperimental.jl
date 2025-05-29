```julia
histcounts!(N, x, xedges::AbstractRange)
```

単純な1Dヒストグラム; `histcounts`と同様ですが、インプレースで、Array `N`の最初の`length(xedges)-1`要素にカウントを追加します。

カウントは`N`に追加され、`N`を上書きすることはないため、累積ヒストグラムを生成することができます。ただし、これは最初の使用前に`N`をゼロで初期化する必要があることを意味します。
