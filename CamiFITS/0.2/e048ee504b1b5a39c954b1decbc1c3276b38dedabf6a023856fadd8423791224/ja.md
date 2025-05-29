```
fits_terminology([term::String [; test=false]])
```

[FITS標準](https://fits.gsfc.nasa.gov/fits_standard.html)からの*定義された用語*の説明：

ANSI、ASCII、ASCII NULL、ASCII文字、ASCII数字、ASCIIスペース、ASCIIテキスト、配列、配列値、基本FITS、ビッグエンディアン、ビット、バイト、カードイメージ、文字列、準拠拡張、データブロック、非推奨、エントリ、拡張、拡張タイプ名、FITS、FITSサポートオフィス、FITSブロック、FITSファイル、FITS構造、フィールド、ファイル、浮動小数点、分数、グループパラメータ値、HDUヘッダーおよびデータユニット、ヘッダー、ヘッダーブロック、ヒープ、IAU、IAUFWG、IEEE、IEEE NaN、IEEE特別値、インデックス付きキーワード、キーワード名、キーワードレコード、MEF、必須キーワード、仮数、NOST、物理値、ピクセル、プライマリHDU、プライマリデータ配列、プライマリヘッダー、ランダムグループ、レコード、繰り返しカウント、予約キーワード、SIF、特別レコード、標準拡張。

```
julia> fits_terminology()
FITS定義用語：
ANSI、ASCII、ASCII NULL、ASCII文字、...、SIF、特別レコード、標準拡張。

julia> fits_terminology("FITS")
FITS：
柔軟な画像輸送システム。

julia> get(dictDefinedTerms, "FITS", nothing)
"柔軟な画像輸送システム。"

julia> fits_terminology("p")
p：
FITS定義用語の1つではありません。
提案：物理値、ピクセル、プライマリHDU、プライマリデータ配列、プライマリヘッダー。

FITS標準を参照 - https://fits.gsfc.nasa.gov/fits_standard.html
```
