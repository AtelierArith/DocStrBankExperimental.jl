```
Xa,xa = EnSRF(Xf,HXf,y,R,H,...)
```

予測アンサンブル `Xf` と観測 `y` を使用して、EnSRFアンサンブルスキームに基づいて分析アンサンブル `Xa` を計算します。

# 入力引数:

  * `Xf`: 予測アンサンブル (n x N)
  * `HXf`: アンサンブルに適用された観測オペレーター (積 H*Xf)
  * `y`: 観測 (m)
  * `R`: 観測誤差共分散 (m x m).
  * `H`: オペレーター (m x n)。serialEnSRFを除いて、これは決して使用されず、空にすることができます。

# オプションのキーワード引数:

  * `debug`: デバッグを有効にするにはtrueに設定します。デフォルト（false）はデバッグなしです。
  * `tolerance`: デバッグチェックのための期待される丸め誤差（デフォルト1e-10）。debugがfalseの場合、これは使用されません。

# 出力引数:

  * `Xa`: 分析アンサンブル (n x N)
  * `xa`: 分析アンサンブル平均 (n)

表記は次の通りです: Sangoma D3.1 http://data-assimilation.net/Documents/sangomaDL3.1.pdf
