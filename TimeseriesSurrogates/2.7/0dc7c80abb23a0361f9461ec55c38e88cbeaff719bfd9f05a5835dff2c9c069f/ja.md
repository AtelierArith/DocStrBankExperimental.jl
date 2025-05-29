```
PseudoPeriodic(d, τ, ρ, shift = true)
```

擬似周期信号に適した代理データを作成します。これらは信号の周期的構造を保持しながら、適切な `ρ` の選択により、決定論的または相関ノイズの間のダイナミクスを破壊します。したがって、これらの代理データは、信号が相関のないノイズを伴う周期軌道であるという帰無仮説をテストするのに適しています[^Small2001]。

引数 `d, τ, ρ` は論文と同様に、埋め込み次元、遅延時間、ノイズ半径を表します。この手法は、DelayEmbeddings.jl からの遅延座標埋め込みを実行することによって機能します（適切な `d, τ` を選択するためのドキュメントを参照してください）。`ρ` については、関数 [`noiseradius`](@ref) において論文で提案された手法を実装しています。

引数 `shift` は論文では議論されていません。`shift=false` の場合、元のデータと代理データの周期成分の間にほとんど位相シフトがないようにアルゴリズムを調整します。

また、[`CycleShuffle`](@ref) も参照してください。

[^Small2001]: Small et al., Surrogate test for pseudoperiodic time series data, [Physical Review Letters, 87(18)](https://doi.org/10.1103/PhysRevLett.87.188101)
