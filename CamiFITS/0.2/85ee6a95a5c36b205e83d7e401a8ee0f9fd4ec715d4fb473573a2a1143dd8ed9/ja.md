```
fits_collect(fileStart::String, fileStop::String [; protect=true [, msg=true]])
```

"fileStart" を "fileStop" と結合します（必須の ".fits" 拡張子付き）

キー:

  * `protect::Bool`: 上書き保護
  * `msg::Bool`: ステータスメッセージを許可

#### 例:

```
julia> for i=1:5
           data = [0 0 0; 0 i 0; 0 0 0]
           fits_create("T$i.fits", data; protect=false)
       end

julia> f = fits_collect("T1.fits", "T5.fits"; protect=false);
'T1-T5.fits': ファイルが作成されました

julia> fits_info(f)[:,:,2]

ファイル: T1-T5.fits
hdu: 1
hdutype: 'PRIMARY '
DataType: Int64
Datasize: (3, 3, 5)

メタ情報:
SIMPLE  =                    T / ファイルは FITS 標準に準拠しています
BITPIX  =                   64 / データピクセルあたりのビット数
NAXIS   =                    3 / データ軸の数
NAXIS1  =                    3 / データ軸 1 の長さ
NAXIS2  =                    3 / データ軸 2 の長さ
NAXIS3  =                    5 / データ軸 3 の長さ
EXTEND  =                    T / FITS データセットには拡張が含まれる可能性があります
END

3×3 Matrix{Int64}:
 0  0  0
 0  2  0
 0  0  0

julia> for i = 1:5 rm("T$i.fits") end

julia> rm("T1-T5.fits"); f = nothing
```
