```
read_buffer(buffer::Vector{UInt8}; channels::AbstractString, startdate::DateTime, enddate::DateTime, headers_only=false, time_tolerance=nothing, verbose_level=0) -> tracelist
```

`buffer`（バイトの系列）内のデータをminiSEEDデータとして解析し、データを含む`tracelist`（`MseedTraceList`）を返します。

`buffer`が有効なminiSEEDデータでない場合、エラーがスローされます。

`channels`には、ファイル内のチャネルの'id'文字列に一致するグロビングパターンを含めることができ、形式は`"FDSN:NET_STA_CHA_BAND_SOURCE_POSITION"`（FDSNソースID; http://docs.fdsn.org/projects/source-identifiers/en/v1.0/）になります。デフォルトでは、すべてのチャネルが読み取られます。

データを`startdate`から`enddate`の範囲に制限するには、これらをキーワード引数として渡します。`startdate`または`enddate`のいずれか一方のみが設定されている場合、それぞれ`enddate`と`startdate`はオープンのままになります。デフォルトは、すべての時間帯からデータを読み取ることです。

!!! 一部のデータは`startdate`より前または`enddate`より後のものが含まれる場合があります。これは、全体のブロックのみが返されるためです。読み取った後にデータをカットして、希望する時間ウィンドウの外にサンプルが存在しないことを確認する必要があります。

`channels`に一致するレコードがない場合、または選択したチャネルのすべてのデータが`startdate`から`enddate`の外にある場合、空のtracelistが返されます。

デフォルトでは、名目上のサンプリング間隔の半分未満のギャップを持つトレースセグメントは結合されて単一のセグメントを形成します。この動作は、秒単位の値を`time_tolerance`に渡すことで調整でき、その場合、`time_tolerance`秒未満のギャップを持つセグメントが結合されます。ギャップを持つセグメントをマージしないには、`time_tolerance = 0`を渡します。

!!! note
    `time_tolerance`はx86およびx64プラットフォームでのみ使用できます。Apple SiliconのようなPowerPCまたはARMプロセッサでは使用できません。これらのプラットフォームのユーザーは、デフォルトの動作を受け入れ、デフォルトの許容範囲よりも大きなギャップで分離されたセグメントを手動で結合する必要があります。詳細はhttps://docs.julialang.org/en/v1/manual/calling-c-and-fortran-code/#Closure-cfunctionsを参照してください。


`verbose_level`は、冗長性レベルを制御するために`libmseed`ルーチン`mstl3_readbuffer`に渡され、`0`（デフォルト）はエラーメッセージのみをstderrに書き込み、より高い数値はより多くの情報を印刷します。
