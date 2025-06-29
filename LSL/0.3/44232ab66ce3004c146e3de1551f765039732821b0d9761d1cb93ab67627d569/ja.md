```
StreamInfo(name = "untitled";
           type = "", 
           channel_count = 1,
           nominal_srate = LSL_IRREGULAR_RATE,
           channel_format = Float32,
           source_id = "")
```

新しいストリーム情報オブジェクトを構築します。

コアストリーム情報はここで指定されます。残りのメタデータは後で追加できます。

# キーワード引数

  * `name::String`: ストリームの名前。プログラム、実験者、またはデータアナリストが使用できるこのストリームが提供するデバイス（または製品シリーズ）を説明します。空にすることはできません。
  * `type::String`: ストリームのコンテンツタイプ。事前定義されたコンテンツタイプ名については https://github.com/sccn/xdf/wiki/Meta-Data を参照するか、ウェブ検索で「XDFメタデータ」を検索してください。ただし、自分自身で作成することもできます。コンテンツタイプは、名前で検索するのではなく、ストリームを見つけるための推奨方法です。
  * `channel_count::Integer`: サンプルごとのチャンネル数。この数はストリームの寿命の間一定です。
  * `nominal_srate::Number`: データソースによって広告されたサンプリングレート（Hz単位）、定期的な場合（そうでない場合は LSL*IRREGULAR*RATE に設定）。
  * `channel_format::DataType`: 各チャンネルのフォーマット/タイプ。チャンネルのフォーマットが異なる場合は、複数のストリームを提供するか、すべてを保持できる最大のタイプ（例えば Float64）を使用することを検討してください。
  * `source_id::String`: 利用可能な場合、ソースまたはデバイスの一意の識別子（シリアル番号など）。受信者が、提供アプリやデバイスがクラッシュした後でも障害から回復できるようにします。場合によっては、デバイス設定から構築されることもあります。
