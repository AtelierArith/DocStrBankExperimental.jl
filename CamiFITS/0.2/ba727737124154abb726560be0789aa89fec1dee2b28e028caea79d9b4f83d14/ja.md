```
fits_read(filnam::String)
```

`.fits` ファイルを読み込み、`FITS_HDU` の配列を返します。

![Image](../assets/fits_read.png)

#### 例:

```
julia> filnam = "minimal.fits";

julia> fits_create(filnam; protect=false);

julia> f = fits_read(filnam);

julia> fits_info(f)
hdu: 1
hdutype: PRIMARY
DataType: Any
Datasize: (0,)

メタ情報:
SIMPLE  =                    T / ファイルは FITS 標準に準拠しています
BITPIX  =                   64 / データピクセルあたりのビット数
NAXIS   =                    1 / データ軸の数
NAXIS1  =                    0 / データ軸 1 の長さ
BZERO   =                  0.0 / データ範囲を符号なし整数の範囲にオフセット
BSCALE  =                  1.0 / デフォルトのスケーリング係数
EXTEND  =                    T / FITS データセットには拡張が含まれる場合があります
END

Any[]

julia> rm(filnam); f = nothing
```
