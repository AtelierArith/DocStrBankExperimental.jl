```
metadata(nmrdata, key)
metadata(nmrdata, dim, key)
metadata(nmrdimension, key)
```

指定されたキーのメタデータを返します。見つからない場合は `nothing` を返します。キーはシンボルとして渡されます。

# 例 (スペクトルメタデータ)

  * `:ns`: スキャンの数
  * `:ds`: ダミースキャンの数
  * `:rg`: 受信ゲイン
  * `:ndim`: 次元の数
  * `:title`: スペクトルタイトル（タイトルpdataファイルの内容）
  * `:filename`: スペクトルファイル名
  * `:pulseprogram`: 取得に使用されたパルスプログラムのタイトル
  * `:experimentfolder`: 実験へのパス
  * `:noise`: RMSノイズレベル

# 例 (次元メタデータ)

  * `:pseudodim`: 非周波数領域データを示すフラグ
  * `:npoints`: 次元内の最終的な（実際の）データポイントの数（抽出後）
  * `:td`: 取得された複素数ポイントの数
  * `:tdzf`: FTが実行されたときの複素数ポイントの数、LPおよびZFを含む
  * `:bf`: 基本周波数（MHz単位）
  * `:sf`: キャリア周波数（MHz単位）
  * `:offsethz`: bfからのキャリアオフセット（Hz単位）
  * `:offsetppm`: bfからのキャリアオフセット（ppm単位）
  * `:swhz`: スペクトル幅（Hz単位）
  * `:swppm`: スペクトル幅（ppm単位）
  * `:region`: 抽出された領域、ポイントの範囲として表現され、そうでなければ欠落
  * `:window`: 適用されたアポダイゼーションを示す `WindowFunction`
  * `:referenceoffset`: 次元に適用された参照（ppm単位）

[`estimatenoise!`](@ref) も参照してください。
