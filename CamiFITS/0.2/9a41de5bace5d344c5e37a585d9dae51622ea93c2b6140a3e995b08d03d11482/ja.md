```
fits_record_dump(filnam [, hduindex=0 [; hdr=true [, dat=true [, nr=true [, msg=true]]]])
```

ファイル `filnam` は、80文字の文字列（レコード）の `Vector{String}` で、さらなるフォーマットはありません。

`msg=true` の場合、`filnam` のリストを36の（オプションでインデックス付きの）レコードのブロック（2880バイト）で出力します。ダンプは*FITSオブジェクトのキャスティングなし*で進行します。すなわち、*FITS適合テストなし*です。

デフォルト: `hduindex` = 0 - すべてのブロック          `hduindex` > 0 - 指定された `hduindex` のみのブロック

  * `hduindex`: HDUインデックス (::Int - デフォルト: `0` すべてのレコード)
  * `hdr`: ヘッダーを表示 (::Bool - デフォルト: true)
  * `dat`: データを表示 (::Bool - デフォルト: true)
  * `nr`: レコードインデックス（行番号）を含める (::Bool - デフォルト: true)
  * `msg`: メッセージを印刷 (::Bool)

注: ツール `fits_record_dump` は、*CamiFITS* パッケージのコード分析を容易にするために開発者向けに含まれています（例: `ENDIAN` ラップの正しい実装やゼロオフセットシフト）。

#### 例:

```
julia> filnam = "foo.fits";

julia> data = [typemin(UInt32),typemax(UInt32)];

julia> fits_create(filnam, data; protect=false);

julia> dump = fits_record_dump(filnam; msg=false);

julia> foreach(println,dump[3:8])
   3 | NAXIS   =                    1 / データ軸の数
   4 | NAXIS1  =                    2 / データ軸1の長さ
   5 | BSCALE  =                  1.0 / デフォルトのスケーリング係数
   6 | BZERO   =           2147483648 / 符号なし整数のデータ範囲にオフセット
   7 | EXTEND  =                    T / FITSデータセットには拡張が含まれる可能性があります
   8 | END

julia> dump[37]
"  37 | UInt8[0x80, 0x00, 0x00, 0x00, 0x7f, 0xff, 0xff, 0xff, 0x00, 0x00, 0x00, ⋯, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00]"]"

julia> rm(filnam); f = data = dump = nothing
```
