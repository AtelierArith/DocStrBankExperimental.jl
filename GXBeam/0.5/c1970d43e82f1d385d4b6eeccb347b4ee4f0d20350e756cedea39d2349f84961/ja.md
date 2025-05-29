```
discretize_beam(start, stop, discretization; frame, curvature)
```

`start`から`stop`までのビームを、`discretization`で提供された離散化に従って離散化します。

ビーム要素の長さ、端点、中点、および参照フレームを返します。

# 引数

  * `start`: ビームの開始点
  * `stop`: ビームの終了点
  * `discretization`: ビーム要素の数、または各ビーム要素の正規化された端点で、値は0から1の範囲です。

# キーワード引数

  * `frame`: ビーム要素の開始時の参照フレームで、変形していないローカルフレームからボディフレームへの3x3変換行列で表されます。
  * `curvature`: 曲率ベクトル
