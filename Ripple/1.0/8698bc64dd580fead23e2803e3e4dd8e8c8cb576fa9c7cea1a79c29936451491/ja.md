```
function read_nev(fname::String)
```

NEVファイル`fname`を読み込み、[`NEVFile`](@ref)を返します。

このメソッドはまだ構築中です。いくつかの拡張ヘッダーとパケットタイプはまだ実装されていません。

このメソッドは、Rippleの[ドキュメント](https://rippleneuro.s3-us-west-2.amazonaws.com/downloads/documentation/NEVspec2_2_v07.pdf)に指定されたNEV 2.2ファイルフォーマットに基づいています。
