```
salt_pepper_chn(X; salt_prob=0.5, salt=1.0, pepper=0.0[, prob=0.1])
```

RGB画像`X`に塩と胡椒のノイズが影響を与えます。塩または胡椒が発生すると、それはRGBのすべてのチャンネルに適用され、画像全体に本物の塩と胡椒が現れます。`prob`は、ピクセルがノイズの影響を受ける確率のためのオプション引数です。`salt_prob`は塩ノイズの確率を表すキーワード引数です。したがって、胡椒ノイズの確率は1-`salt_prob`です。`salt`は塩ノイズの値を指定するためのキーワード引数です。`pepper`は胡椒ノイズの値を指定するためのキーワード引数です。
