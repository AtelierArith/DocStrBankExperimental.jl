```
Upsample(mode = :nearest; [scale, size, align_corners=false])
Upsample(scale, mode = :nearest)
```

アップサンプリングレイヤー。

## レイヤー構築

### オプション 1

  * `mode`: `:nearest`、`:linear`、`:bilinear` または `:trilinear` に設定

2つのキーワードのうち、正確に1つを指定する必要があります：

  * `scale` が数値の場合、これは入力の最後の2次元（チャネルとバッチ）を除くすべてに適用されます。また、次元を個別に制御するためにタプルであることもできます。
  * あるいは、キーワード `size` はタプルを受け入れ、出力の先頭次元を直接指定します。

### オプション 2

  * `scale` が数値の場合、これは入力の最後の2次元（チャネルとバッチ）を除くすべてに適用されます。また、次元を個別に制御するためにタプルであることもできます。
  * `mode`: `:nearest`、`:bilinear` または `:trilinear` に設定

現在サポートされているアップサンプリング `mode` と対応する NNlib のメソッドは次のとおりです：

  * `:nearest` -> `NNlib.upsample_nearest`
  * `:bilinear` -> `NNlib.upsample_bilinear`
  * `:trilinear` -> `NNlib.upsample_trilinear`

# 拡張ヘルプ

## その他のキーワード引数

  * `align_corners`: `true` の場合、入力と出力のテンソルのコーナーピクセルが整列し、したがってそれらのピクセルの値が保持されます。これは、モードが `:bilinear` または `:trilinear` のいずれかである場合にのみ効果があります。

## 入力

  * `x`: 入力次元については、対応する `NNlib` 関数のドキュメントを参照してください

      * 一般的なルールとして、`:nearest` は任意の次元の配列で機能するはずです
      * `:bilinear` は4D配列で機能します
      * `:trilinear` は5D配列で機能します

## 戻り値

  * サイズ `size` またはサイズ `(I_1 x scale[1], ..., I_N x scale[N], C, N)` のアップサンプリングされた入力
  * 空の `NamedTuple()`
