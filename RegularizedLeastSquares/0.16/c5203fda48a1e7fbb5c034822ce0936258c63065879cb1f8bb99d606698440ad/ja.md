```
TV正則化
```

正則化項は、TV正則化のための近接写像を実装しています。TVが1つの実数値次元に沿ってのみ計算される場合はCondatアルゴリズムで計算され、それ以外の場合は高速勾配投影アルゴリズムで計算されます。

Condatアルゴリズムの参考文献: https://lcondat.github.io/publis/Condat-fast_TV-SPL-2013.pdf

FGPアルゴリズムの参考文献: A. Beck and T. Teboulle, "Fast Gradient-Based Algorithms for Constrained Total Variation Image Denoising and Deblurring Problems", IEEE Trans. Image Process. 18(11), 2009

# 引数

  * `λ::T`                    - 正則化パラメータ

# キーワード

  * `shape::NTuple`           - 基本画像のサイズ
  * `dims`                    - TVを実行する次元。`Integer`の場合、Condatアルゴリズムが呼び出され、それ以外の場合はFDGアルゴリズムが呼び出されます。
  * `iterationsTV=20`         - FGPの反復回数
