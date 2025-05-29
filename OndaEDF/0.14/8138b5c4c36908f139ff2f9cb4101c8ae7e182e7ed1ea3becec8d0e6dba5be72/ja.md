```
onda_to_edf(samples::AbstractVector{<:Samples}, annotations=[]; kwargs...)
```

Onda [`Samples`](https://beacon-biosignals.github.io/Onda.jl/stable/#Samples-1) のコレクションから変換された信号データを含む `EDF.File` を返します。また、（オプションで）[`annotations` テーブル](https://beacon-biosignals.github.io/Onda.jl/stable/#*.onda.annotations.arrow-1) からの注釈も含まれます。

Onda v0.5 形式に従い、`annotations` は [annotation schema](https://beacon-biosignals.github.io/Onda.jl/stable/#*.onda.annotations.arrow-1) に従った任意の Tables.jl 互換テーブル（DataFrame、Arrow.Table、ベクトルの NamedTuple、NamedTuple のベクトル）であることができます。

返される `EDF.File` の各 `EDF.Signal` は、入力 `Onda.Samples` のチャネルに対応します。

出力の `EDF.Signal` の順序は、入力の `Samples` のコレクションの順序と一致します（各チャネルグループ内では、サンプルのチャネルの順序も一致します）。

!!! note
    EDF 信号は Int16 としてエンコードされますが、Onda はさまざまなサンプルタイプの範囲を許可しており、その中には Int16 よりもはるかに高い解像度を提供するものもあります。エクスポート中に、エンコードされた Onda サンプルが直接 Int16 値として表現できない場合、再エンコードが必要になることがあります。この場合、新しいエンコーディング（解像度とオフセット）は、入力 Onda Samples の各 *signal* に実際に存在する最小値と最大値に基づいて選択されます。したがって、Onda 形式のデータセットを EDF にロスレスで往復することが常に可能であるとは限りません。

