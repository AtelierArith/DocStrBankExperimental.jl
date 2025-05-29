function measure_noisy

```
この関数は、ノイズのある読み出しでYaoAPI.measureを模倣します
```

# 引数

  * reg: 測定される量子状態を表す状態ベクトル
  * noise_model: 混乱行列を作成するメソッドを含むErrorModel構造体
  * site (オプション): 測定されるサイト
  * nshots (オプションのキーワード引数): 返される測定の数
