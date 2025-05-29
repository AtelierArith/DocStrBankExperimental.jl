```
fit_spectrum(spec::Spectrum, ffp::FilterFitPacket)::FilterFitResult
fit_spectrum(specs::AbstractVector{<:Spectrum}, ffp::FilterFitPacket)::Vector{FilterFitResult}
fit_spectra(specs::AbstractVector{<:Spectrum}, ffp::FilterFitPacket)::Vector{FilterFitResult}
```

指定された `FilterFitPacket` を使用して `Spectrum` または `Spectrum` のベクトルをフィットします。結果は k-ratio、残差などを含む `FilterFitResult` 構造体です。

```
fit_spectrum(hs::HyperSpectrum, ffp::FilterFitPacket; mode::Symbol=:Fast, zero = x -> max(0.0, x))::Array{KRatios}
```

  * `mode = :Fast` - 事前に計算されたフィルタリングされた「ベクトル」フィット法を使用します。不確実性は利用できません。
  * `mode = :Intermediate` - 負の k-ratio の再フィットなしで最適化されたフルフィットを使用します。
  * `mode = :Full` - 1つ以上の k-ratio がゼロ未満のときに再フィッティングを含むフルシングルスペクトルフィットアルゴリズムを使用します。

ハイパースペクトルに対してフィルタリングされたフィットを実行し、`Array{KRatios}` を返します。

モードの選択: :Fast は k-ratio マップの生成や k-ratio マップの探索的分析に適しています。 :Full は高カウントのハイパースペクトルの定量的マップが必要な場合に最適です。主要元素のフィット結果はすべてのモードで似ていますが、微量元素やトレース元素では異なります。特に k-ratio がわずかに負のとき。この負の k-ratio は他の k-ratio に影響を与える可能性があります。 :Fast は多くの元素 (>>10) (特に干渉元素) がフィットに含まれる場合、あまり効果的ではありません。残念ながら、:Intermediate と :Full は多くの元素がフィットされると遅くなります - O(n(elements)²)。

以下は、16 GiB メモリを搭載した高速 6コアノートパソコンで 33 の異なる ROI を持つ 21 の元素をフィットさせた 512 x 512 x 2048 のハイパースペクトルのタイミングです。各アルゴリズムの速度感を相対的に示します。はい、:Fast は :Intermediate より約 30 倍速く、メモリをほぼ 80 倍少なく使用しました。(64ビット参照、32ビット参照は約 1/2 のメモリを使用し、約 4/5 の時間がかかります。)

|         mode= | Threads | Run time (s) | Allocations | Allocated (GiB) | GC time |
| -------------:| -------:| ------------:| -----------:| ---------------:| -------:|
|         :Fast |       6 |         11.4 |      2.11 M |            4.72 |    3.0% |
| :Intermediate |       6 |        342.7 |     13.11 M |           364.4 |    4.2% |
|         :Full |       6 |        574.6 |       6.2 G |           862.9 |    5.5% |
|         :Fast |       1 |         25.5 |       2.1 M |            4.72 |    1.8% |
| :Intermediate |       1 |       1064.6 |      13.1 M |           364.4 |    0.9% |
|         :Full |       1 |       2186.2 |       6.2 G |           862.1 |    2.8% |
