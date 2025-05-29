```
R = dn2temperature(fname::String; band::Int=0, mtl::String="", save::String)
```

Landsat8の熱バンド（10または11）の輝度温度を計算します。

  * `fname`: $LANDSAT_PRODUCT_ID$のGeoTIFFバンドの名前、または`cutcube`関数で作成されたキューブファイルの名前です。最初のケースでは、$...MTL.txt$ファイルが`fname`と同じディレクトリにない場合でも、`mtl=path-to-MTL-file`オプションを介して渡すことができます。2番目のケースでは、次の2つのオプションのいずれかを使用することが必須です。
  * `band`: [`cutcube`](@ref)で作成された*キューブ*は、「Band 1 ...」で始まる説明を他のバンドに割り当てます。したがって、`band`が使用されると、「Band N」という名前のバンドを検索します。ここで、N = `band`です。
  * `bandname`: バンドの一般的な名称、たとえば「Green」や、バンドの説明の一部、たとえば「NIR」を知っている場合、その情報を使用してキューブのバンドの説明と一致する`bandname`文字列を作成できます。`reportbands`関数を使用してバンドの説明を確認できます。
  * `save`: 出力を保存するファイル名です。指定しない場合、GMTgridが返されます。

Float32 GMTgridを返します。

# 例:

キューブに保存されたバンド10の輝度温度を計算します。

```
T = dn2temperature(cube, band=10)
```
