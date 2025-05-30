```
tablequartetCF(quartetlist::Vector{QuartetT} [, taxonnames];
               keepQwithoutgenes=true, colnames=nothing)
```

[`QuartetT`](@ref) オブジェクトのベクターを、リスト内の各4タクソンセットに対して1行のテーブルに変換します。各4タクソンセットには、テーブルの列数を決定するタイプ `T` のクァルテットデータが含まれています。このデータタイプ `T` は、長さ3または4のベクター、または3×nの行列である必要があります。出力は `NamedTuple` であり、一般的なテーブル操作を [`Table.jl`](https://github.com/JuliaData/Tables.jl) 互換のソースとして適用できます。他のテーブル形式（例：これらのパッケージは [Tables.jl](https://github.com/JuliaData/Tables.jl/blob/master/INTEGRATIONS.md) と統合されています）に簡単に変換できます（例：`DataFrame`）。

出力テーブルの列は、次の順序で構成されています：

  * `qind`: クァルテットの `number` を含みます
  * `t1, t2, t3, t4`: `taxonnames` が指定されていない場合はクァルテットの `taxonnumber` を含み、そうでない場合はタクソン名を含みます。タクソン番号 `i` の名前は `taxonnames[i]` として取られます。
  * クァルテットの `data` に対して3列以上： [`quartetdata_columnnames`](@ref) を参照してください。

要するに、データの最初の3列は `CF12_34, CF13_24, CF14_23` という名前が付けられています。

クァルテットに4つのデータエントリがある場合、4番目の列は `ngenes` という名前が付けられ、値 `ngenes` が0のクァルテットはテーブルからスキップ（除外）されます。ただし、`keepQwithoutgenes=true` の場合は除外されません（デフォルトはこれです：情報のある遺伝子がなくても4タクソンセットはデフォルトで保持されます）。

クァルテットに3行と `d` 列のデータ行列がある場合、テーブルの列4,5,6は `V2_12_34, V2_13_24, V2_14_23` という名前が付けられ、クァルテットのデータ行列の2列目のデータを含みます。以下同様です。

テーブルにデフォルト以外の列名を持たせるには、オプション引数 `colnames` を介して希望する3、4、または3×dの名前をベクターとして提供してください。

例については [`countquartetsintrees`](@ref) を参照してください。
