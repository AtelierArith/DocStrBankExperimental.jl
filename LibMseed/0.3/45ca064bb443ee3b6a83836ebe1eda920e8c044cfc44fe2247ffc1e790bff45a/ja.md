```
write_file(file, data, sample_rate, starttime, id; append=false, verbose_level=0, compress=:steim2, pubversion=1, record_length=nothing) -> n
```

`data`をminiSEED形式で`file`に書き込み、書き込まれたレコードの数`n`を返します。1秒あたりのサンプル数は`sample_rate`で指定されます。

`starttime`は最初のサンプルの日付で、`Dates.DateTime`であるか、1970-01-01T00:00:00以降のナノ秒の整数でなければなりません。

`id`はトレースのIDを示すASCII文字列です。64文字を超える場合は、警告とともに切り捨てられます。

!!! note
    libmseedライブラリは、`id`が`FDSN[:AGENCY]:NET_STA_LOC_BAND_SOURCE_POSITION`の形式であることを要求します。ここで、`NET`はネットワーク、`STA`はステーション、`LOC`は機器の位置コード、`BAND`は記録の周波数帯、`SOURCE`は機器の種類のコード、`POSITION`はコンポーネントの方向のコードを示します。`AGENCY`は情報の出所に関する情報を提供しますが、これは標準ではなく、他のツールがこれらのIDを正しく読み取れない場合があります。デジタル地震計ネットワーク連盟（FDSN）は、フォーマットについてhttp://docs.fdsn.org/projects/source-identifiers/en/v1.0/で説明しています。

    バージョン2のファイル（書き込みのデフォルト）には、以下の文字制限があります：

      * `NET`: 2
      * `STA`: 5
      * `LOC`: 2
      * `BAND`、`SOURCE`、および`POSITION`: 1

    バージョン3のファイルでは、識別子の合計は255文字未満でなければなりません。


`append=true`を使用して、`file`に新しいレコードを追加します。そうでない場合、既存のファイルは上書きされます。どちらの場合でも、`file`は存在しない場合に作成されます。

`verbose_level`は、`libmseed`ルーチン`mstl3_readtracelist`に渡され、冗長性レベルを制御します。`0`（デフォルト）はエラーメッセージのみをstderrに書き込み、より高い数値はより多くの情報を印刷します。

# 許可される`data`要素タイプ

miniSEEDファイルには、`Int32`、`Float32`、または`Float64`の要素タイプのデータのみを含めることができます。したがって、この関数はこれらの要素タイプのいずれかを持つベクトルのみを書き込み、異なるタイプが渡された場合はエラーをスローします。この関数を呼び出す前に、データをこれらのタイプのいずれかに変換する必要があります。

# 圧縮オプション

`compress`は`:steim1`または`:steim2`の値を取ることができ、それぞれSteim-1またはSteim-2圧縮でファイルが書き込まれます。これは`Int32`データに対してのみ可能です。

# miniSEEDファイルバージョン

miniSEEDファイルで使用される標準バージョンはバージョン2で、書き込みのデフォルトです。ただし、libmseedライブラリは新しいバージョン3をサポートしています。バージョン2は、時間のマイクロ秒精度のみをサポートしていることに注意してください。マイクロ秒の整数で表現できない`starttime`を渡すと、基盤となるlibmseedライブラリは、指定された時間の下の整数マイクロ秒に時間を切り捨てます。

# すべてのキーワード引数

  * `append = false`: `true`の場合、既存のファイルが存在する場合はこのデータを追加します。
  * `verbose_level = 0`: libmseedライブラリの冗長性を制御し、0より大きい値は冗長性を増加させます。
  * `compress = :steim2`: 入力データが整数の場合、データを書き込む際にSteim圧縮を使用します。オプションは`:steim1`（Steim-1圧縮）と`:steim2`（Steim-2圧縮）です。
  * `pubversion = 1`: レコードの公開バージョンを設定します。SEEDでは、後のバージョンは修正されたデータに対応し、以前のバージョンよりもファイルから優先的に読み取られます。
  * `record_length = nothing`: ディスクに書き込まれるレコードの長さを制御します。デフォルトではlibmseedライブラリがレコードの長さを決定します。
  * `version = 2`: 書き込むminiSEEDファイルのバージョン（`2`または`3`）。現在のバージョン`3`をサポートするソフトウェアはほとんどないため、デフォルトはバージョン`2`を書き込むことです。

# 例

```
julia> using Dates: DateTime

julia> data = rand(Float32, 1000);

julia> sampling_rate = 100;

julia> starttime = DateTime("2000-01-01");

julia> id = "FDSN:GB_JSA__B_H_Z";

julia> LibMseed.write_file("data.mseed", data, sampling_rate, starttime, id)
1

julia> LibMseed.read_file("data.mseed")
MseedTraceList:
 1 trace:
  "FDSN:GB_JSA__B_H_Z": 2000-01-01T00:00:00.000000000 2000-01-01T00:00:09.990000000, 1 segments
```
