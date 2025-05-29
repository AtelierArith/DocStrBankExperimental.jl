```
fits_rename_key!(filnam::String, hduindex::Int, keyold::String, keynew::String)
```

ファイル名 'filnam' のヘッダーレコードのキーを変更します。

#### 例:

```
julia> filnam="minimal.fits";

julia> f = fits_create(filnam; protect=false);

julia> fits_add_key!(f, 1, "KEYNEW1", true, "this is a new record");

julia> fits_rename_key!(f, 1, "KEYNEW1",  "KEYNEW2");

julia> fits_info(f.hdu[1])
hdu: 1
hdutype: 'PRIMARY '
DataType: Any
Datasize: (0,)

メタ情報:
SIMPLE  =                    T / ファイルはFITS標準に準拠しています
BITPIX  =                   64 / データピクセルあたりのビット数
NAXIS   =                    1 / データ軸の数
NAXIS1  =                    0 / データ軸1の長さ
BZERO   =                  0.0 / データ範囲を符号なし整数の範囲にオフセット
BSCALE  =                  1.0 / デフォルトのスケーリングファクター
EXTEND  =                    T / FITSデータセットには拡張が含まれる場合があります
COMMENT    拡張FITS HDU   / http://fits.gsfc.nasa.gov/
KEYNEW2 =                    T / これは新しいレコードです
END

Any[]
```
