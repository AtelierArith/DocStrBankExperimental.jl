```
ExpAndGram{T,N,A,B,C} <: AbstractExpAndGramAlgorithm
```

行列指数関数と関連するグラミアンを計算するための非適応アルゴリズムの順序 N。

コンストラクタ：

ExpAndGram{T,N}()

順序 N の数値型 T に格納された係数を持つアルゴリズムを作成します。現在サポートされている N の値は 3, 5, 7, 9, 13 です。
