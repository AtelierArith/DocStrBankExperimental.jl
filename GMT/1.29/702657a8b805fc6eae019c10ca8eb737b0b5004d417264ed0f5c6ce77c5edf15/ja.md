```
[I =] grays2cube(layers::GMTimage{UInt8,2}...; names::Vector{String}=String[], save::String="") -> GMTimage
```

N個のグレースケールUInt8 GMT画像を取り込み、画像キューブに集約します。各レイヤーの名前のベクターをオプションで提供できます。`save`オプションが提供されると、キューブをGeoTIFFファイルとして保存します。出力名は常に'*.tiff'になるため、拡張子を提供する必要はありません。

### 例

```juliadoc
# RGB画像のYCbCRおよびLa*b*カラースペースのCb、Cr、a*、b*成分を持つキューブを作成
I = mat2image(rand(UInt8,128, 128, 3))		# サンプルRGB画像を作成
_,Cb,Cr = rgb2YCbCr(I, Cb=true, Cr=true);	# CbおよびCr成分を抽出
L,a,b   = rgb2lab(I, L=true);				# La*b*成分を抽出
Icube = grays2cube(Cb, Cr, a, b; names=["Cb", "Cr", "a", "b"]);
```
