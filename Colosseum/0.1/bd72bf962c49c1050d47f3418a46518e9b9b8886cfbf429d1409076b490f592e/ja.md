単一の画像を取得します。png形式の画像のバイトを返し、バイナリファイルにダンプして.png画像を作成できます。`string_to_uint8_array()`を使用してNumpyのunit8配列に変換できます。詳細については、https://microsoft.github.io/AirSim/image*apis/を参照してください。

引数:

  * camera*name (str) カメラの名前。後方互換性のため、ID番号（0,1など）も使用できます。
  * image*type (ImageType) 必要な画像のタイプ。
  * vehicle*name (str, optional) カメラを持つ車両の名前。
  * external (bool, optional) カメラが外部カメラであるかどうか。

戻り値:

  * 圧縮されたpng画像のバイナリ文字列リテラル。
