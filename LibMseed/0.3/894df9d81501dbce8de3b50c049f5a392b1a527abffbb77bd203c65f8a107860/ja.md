```
read_file(file; channels::AbstractString, startdate::DateTime, enddate::DateTime, headers_only=false, time_tolerance=nothing, verbose_level=0) -> tracelist
```

ディスク上の `file` から miniSEED データを読み取り、データを含む `tracelist`（`MseedTraceList`）を返します。`headers_only` が `true` の場合、ヘッダーのみが読み込まれ、データは展開されません。この場合、データの要素タイプは計算できず、代わりに `Missing` としてマークされます。

`file` に有効なデータが含まれていない場合、エラーがスローされます。

`channels` には、ファイル内のチャンネルの 'id' 文字列に一致するグロビングパターンを含めることができ、形式は `"FDSN:NET_STA_CHA_BAND_SOURCE_POSITION"` になります（FDSN ソース ID; http://docs.fdsn.org/projects/source-identifiers/en/v1.0/）。デフォルトでは、すべてのチャンネルが読み込まれます。

データを `startdate` から `enddate` までの期間におおよそ制限するには、これらをキーワード引数として渡します。`startdate` または `enddate` のいずれか一方のみが設定されている場合、それぞれ `enddate` と `startdate` はオープンのままになります。デフォルトは、すべての時間帯からデータを読み込むことです。

!!! 一部のデータは `startdate` より前または `enddate` より後のものが含まれる可能性があります。これは、全体のブロックのみが返されるためです。読み込んだ後にデータをカットして、希望する時間ウィンドウの外にサンプルが存在しないことを確認する必要があります。

`channels` に一致するレコードがない場合、または選択したチャンネルのすべてのデータが `startdate` から `enddate` の外にある場合、空の tracelist が返されます。基盤となる libmseed ライブラリも stdout にエラーを出力します。これは誤りであり、残念ながら避けられません。

デフォルトでは、名目上のサンプリング間隔の半分未満のギャップを持つトレースセグメントは結合されて単一のセグメントを形成します。この動作は、秒単位の値を `time_tolerance` に渡すことで調整でき、その場合、`time_tolerance` 秒未満のギャップを持つセグメントが結合されます。ギャップを持つセグメントをマージしないには、`time_tolerance = 0` を渡します。

!!! note
    `time_tolerance` は x86 および x64 プラットフォームでのみ使用できます。PowerPC や Apple Silicon のような ARM プロセッサでは使用できません。これらのプラットフォームのユーザーは、デフォルトの動作を受け入れ、デフォルトの許容範囲よりも大きなギャップで分離されたセグメントを手動で結合する必要があります。詳細は https://docs.julialang.org/en/v1/manual/calling-c-and-fortran-code/#Closure-cfunctions を参照してください。


`verbose_level` は、冗長性レベルを制御するために `libmseed` ルーチン `mstl3_readtracelist_selection` に渡され、`0`（デフォルト）はエラーメッセージのみを stderr に書き込み、より高い数値はより多くの情報を出力します。
