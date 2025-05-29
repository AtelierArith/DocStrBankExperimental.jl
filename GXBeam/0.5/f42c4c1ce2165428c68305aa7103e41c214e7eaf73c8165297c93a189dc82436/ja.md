```
discretize_beam(L, start, discretization; frame, curvature)
```

長さ `L` のビームを `start` に位置させ、`discretization` で提供された離散化に従って離散化します。

ビーム要素の長さ、端点、中点、および参照フレームを返します。

# 引数

  * `L`: ビームの長さ
  * `start`: ビームの開始点
  * `discretization`: ビーム要素の数、または各ビーム要素の正規化された端点で、値は 0 から 1 の範囲です。

# キーワード引数

  * `frame`: ビーム要素の開始時の参照フレームで、変形していないローカルフレームからボディフレームへの 3x3 の変換行列で表されます。
  * `curvature`: 曲率ベクトル

```
