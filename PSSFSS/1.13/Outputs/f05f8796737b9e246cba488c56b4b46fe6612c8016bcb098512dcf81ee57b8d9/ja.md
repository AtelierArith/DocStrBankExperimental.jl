```
res2tep(results::Vector{Result}; name="tep", class="res2tep") -> t::TEPperiodic
res2tep(resultfile::AbstractString; name="tep", class="res2tep") -> t::TEPperiodic
res2tep(results::Vector{Result}, tepfile::AbstractString; name="tep", class="res2tep") -> t::TEPperiodic
res2tep(resultfile::AbstractString, tepfile::AbstractString; name="tep", class="res2tep") -> t::TEPperiodic
```

`Result` 要素のベクトルを `TEPperiodic` オブジェクトに変換します。これは、[TicraUtilities](https://github.com/simonp0420/TicraUtilities.jl) パッケージで定義されています。位置引数 `tepfile` が提供されると、`TEPperiodic` オブジェクトはこのファイル名に TICRA 互換の TEP（表形式電気特性）ファイルとして保存されます。最初の位置引数が `AbstractString` の場合、それは PSSFSS 結果ファイルの名前であると見なされ、結果のベクトルがそこから読み込まれます。キーワード引数は、TEP 構造内の同名のフィールドに値を提供するために使用されます。

## TEP ファイル互換性の要件

TEP ファイルには PSSFSS によって計算された完全な 4×4 散乱行列のすべての情報が含まれているため、TEP ファイルを作成するために使用できる単位セルジオメトリのタイプに制限はありません。

TEP ファイルは「前面」と「背面」の入射の概念を使用します。PSSFSS 分析結果を TEP 形式に変換する際、領域 1（`strata` ベクトルの最初の層）は「前面」入射領域と見なされ、領域 `n`（最後の層）は「背面」領域と見なされます。これらの層はどちらも幅がゼロで、真空の電気パラメータを仮定する必要があります。すなわち、`strata` スタックアップ内で `Layer()` として指定されるべきです。

`results`（または `resultfile`）は、θ および ϕ（および場合によっては周波数）に対する PSSFSS 分析スイープの結果を含む必要があります。

1. 入射角 θ および ϕ が、増分位相 ψ₁ および ψ₂ ではなく使用されました。
2. 1 つ以上の ϕ 値が使用される場合、範囲 `0:Δϕ:(360-Δϕ)` 内のすべての ϕ 値が存在する必要があります。
3. すべての角度と周波数の 3 次元カルテジアン積が存在する必要があります。
