```
XPRS_MIPKAPPAFREQ
```

分岐と境界: 分岐と境界探索中に基準条件数（カッパとも呼ばれる）をどのくらいの頻度で計算するかを指定します。（整数）

デフォルト値: `0`

値: 0 : 条件数を計算しない。 1 : 各ノードで条件数を計算し、ルートカッティングの各ラウンド後も含む。 n>1 : 分岐と境界ツリーの各 n 番目のレベルのノードごとに一度条件数を計算する。
