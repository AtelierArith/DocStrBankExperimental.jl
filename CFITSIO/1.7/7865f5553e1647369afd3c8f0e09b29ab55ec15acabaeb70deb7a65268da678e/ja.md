```
fits_movnam_hdu(f::FITSFile, extname::String, extver::Integer=0,
                hdu_type_int::Integer=-1)
```

指定された拡張タイプとEXTNAMEおよびEXTVERキーワード値（またはHDUNAMEおよびHDUVERキーワード）を持つ（最初の）HDUに移動することによって、現在のHDUを変更します。

`extver`が0（デフォルト）である場合、EXTVERキーワードは無視され、マッチするEXTNAME（またはHDUNAME）キーワードを持つ最初のHDUが見つかります。`hdu_type_int`が-1（デフォルト）の場合、正しい拡張を見つけるためにextnameおよびextverの値のみが使用されます。ファイル内に一致するHDUが見つからない場合、現在のHDUは変更されません。
