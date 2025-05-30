```
LucasKanade(Args...)
```

ブルース・D・ルーカスと武田健男によって開発された光フロー推定のための微分法です。これは、考慮中のピクセルの局所的な近傍でフローが本質的に一定であると仮定し、最小二乗基準によってその近傍内のすべてのピクセルに対して基本的な光フロー方程式を解きます。

# オプション

このタイプのフィールドに関するさまざまなオプションが以下で詳しく説明されています。

## `iterations` の選択肢

反復検索アルゴリズムの終了基準、すなわち反復の回数です。

## `window_size` の選択肢

各ピラミッドレベルでの検索ウィンドウのサイズ; 使用されるウィンドウの合計サイズは 2*window_size + 1 です。指定しない場合、デフォルト値は11と見なされます。

## `pyramid_levels` の選択肢

0ベースの最大ピラミッドレベル番号; 0に設定するとピラミッドは使用されず（単一レベル）、1に設定すると2レベルが使用され、以下同様です。指定しない場合、デフォルト値は4と見なされます。

## `eigenvalue_threshold` の選択肢

アルゴリズムは、光フロー方程式の (2 x 2) 正規行列の最小固有値を計算し、ウィンドウ内のピクセル数で割ります。この値が `eigenvalue_threshold` より小さい場合、対応する特徴はフィルタリングされ、そのフローは処理されません（デフォルト値は1e-4です）。

## `ϵ` 終了基準

反復アルゴリズムが作業を続けるために必要な変位の最小変化。デフォルト値は `1e-2` です。

## 参考文献

1. B. D. Lucas, & Kanade. "An Interative Image Registration Technique with an Application to Stereo Vision," DARPA Image Understanding Workshop, pp 121-130, 1981.
2. J.-Y. Bouguet, “Pyramidal implementation of the afﬁne lucas-kanade feature tracker description of the algorithm,” Intel Corporation, vol. 5,no. 1-10, p. 4, 2001.
