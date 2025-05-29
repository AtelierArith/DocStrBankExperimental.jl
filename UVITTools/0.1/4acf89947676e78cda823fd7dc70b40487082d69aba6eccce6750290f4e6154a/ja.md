`fuv_grating1_count_spec(fuv_grating1_image_file, ds9regfile[, order = -1, angle_xaxis_disp_deg=0.0, cross_disp_width_pixels = 40, rate = true])` 

AstroSat/UVIT FUV-Grating1の分散画像からカウントレートスペクトルを抽出します。これはCCDLAB処理パイプラインから生成されます。

...

# 引数

## 必須パラメータ

  * `fuv_grating1_image_file::String`: CCDLABを使用して生成されたFUV-Grating1画像ファイルのFITS形式の名前。
  * `ds9regfile::String`: ゼロオーダー位置を中心とするds9領域ファイルの名前。

## オプションパラメータ

  * `order::Int`: -2（デフォルト）、スペクトルを抽出するために使用されるグレーティングオーダー。許可されるオーダーは-1と-2です。
  * `angle_xaxis_disp_deg`: 0.0（デフォルト）、分散軸とx軸の間の角度。
  * `cross_disp_width_pixels::String`: 40（デフォルト）、クロス分散方向のピクセル幅。
  * `rate::Bool`: カウントレートスペクトルの場合はtrue（デフォルト）、そうでない場合はカウントスペクトルのためにfalse。

## 出力

  * カウントスペクトルファイル
  * 要求されたオーダーの抽出領域を検証するために使用できるds9と互換性のある領域ファイル。
  * カウントスペクトル（ゼロオーダーに対するピクセル番号、カウント/sまたはカウント、エラー）として。

...
