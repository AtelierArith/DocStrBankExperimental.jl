```
Xa,xa = serialEnSRF(Xf,HXf,y,R,H,...)
```

予測アンサンブル `Xf` と観測 `y` を使用して、serialEnSRF アンサンブルスキームに基づいて分析アンサンブル `Xa` を計算します。

# 入力引数:

  * `Xf`: 予測アンサンブル (n x N)
  * `HXf`: アンサンブルに適用される観測オペレーター (積 H*Xf)
  * `y`: 観測 (m)
  * `R`: 観測誤差共分散 (m x m).
  * `H`: オペレーター (m x n)。serialEnSRF を除いては使用されず、空にすることができます。

# オプションのキーワード引数:

  * `debug`: デバッグを有効にするには true に設定します。デフォルト (false) はデバッグなしです。
  * `tolerance`: デバッグチェックのための期待される丸め誤差 (デフォルト 1e-10)。debug が false の場合は使用されません。

# 出力引数:

  * `Xa`: 分析アンサンブル (n x N)
  * `xa`: 分析アンサンブル平均 (n)

表記は次の通りです: Sangoma D3.1 http://data-assimilation.net/Documents/sangomaDL3.1.pdf
