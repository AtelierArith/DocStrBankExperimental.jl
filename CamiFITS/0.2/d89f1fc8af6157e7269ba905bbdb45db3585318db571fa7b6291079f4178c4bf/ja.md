```
fits_info(f::FITS [, hduindex=1 [; nr=false [, hdr=true]]])
fits_info(hdu::FITS_HDU; nr=false, hdr=true)
```

与えられた [`FITS_HDU`](@ref) オブジェクトのメタ情報とデータ（*オプション* のレコード番号付き）。

  * `hduindex`: HDU インデックス (::Int - デフォルト: `1` = `プライマリ hdu`)
  * `nr`: カードインデックスを含める (::Bool - デフォルト: `false`)
  * `hdr`: ヘッダーを表示 (::Bool)

#### 例:

`fits_info` を示すために、まず後の検査のために fits オブジェクト `f` を作成します。

```
julia> filnam = "minimal.fits";

julia> f = fits_create(filnam; protect=false);

julia> fits_info(f)

File: minimal.fits
hdu: 1
hdutype: 'PRIMARY '
DataType: Any
Datasize: (0,)

メタ情報:
SIMPLE  =                    T / ファイルは FITS 標準に準拠しています
BITPIX  =                   64 / データピクセルあたりのビット数
NAXIS   =                    1 / データ軸の数
NAXIS1  =                    0 / データ軸 1 の長さ
EXTEND  =                    T / FITS データセットには拡張が含まれる場合があります
END

Any[]

julia> rm(filnam); f = nothing
```

```
fits_info(filnam::String [, hduindex=1 [; nr=true [, hdr=true]]])
```

上記と同じですが、ディスクから `filnam` を読み込んで fits オブジェクトを作成し、*デフォルト* のレコード番号付きです。

  * `hduindex`: HDU インデックス (::Int - デフォルト: `1` = `プライマリ hdu`)
  * `nr`: カードインデックスを含める (::Bool - デフォルト: `true`)
  * `hdr`: ヘッダーを表示 (::Bool)

#### 例:

```
julia> filnam = "minimal.fits";

julia> fits_create(filnam; protect=false);

julia> fits_info(filnam)

File: minimal.fits
hdu: 1
hdutype: 'PRIMARY '
DataType: Any
Datasize: (0,)

  nr | メタ情報:
---------------------------------------------------------------------------------------
   1 | SIMPLE  =                    T / ファイルは FITS 標準に準拠しています
   2 | BITPIX  =                   64 / データピクセルあたりのビット数
   3 | NAXIS   =                    1 / データ軸の数
   4 | NAXIS1  =                    0 / データ軸 1 の長さ
   5 | EXTEND  =                    T / FITS データセットには拡張が含まれる場合があります
   6 | END

Any[]

julia> rm(filnam)
```
