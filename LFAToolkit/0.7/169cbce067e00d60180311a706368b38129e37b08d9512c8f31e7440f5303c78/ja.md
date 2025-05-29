```julia
Chebyshev(operator)
```

有限要素演算子のためのチェビシェフ多項式前処理器。チェビシェフ半反復法は、行列 $D^{-1} A$ に適用され、ここで $D^{-1}$ は演算子対角の逆数です。

# 引数:

  * `operator::Operator`: 前処理する有限要素演算子
  * `chebyshevtype::ChebyshevType`: チェビシェフの種類、第一、第四、または最適な第四種

# 戻り値:

  * チェビシェフ前処理器オブジェクト

# 例:

```jldoctest
# セットアップ
mesh = Mesh2D(1.0, 1.0);
mass = GalleryOperator("mass", 4, 4, mesh);

# 前処理器
chebyshev = Chebyshev(mass);

# 検証
println(chebyshev)

# 出力

chebyshev 前処理器:
1種チェビシェフ
固有値の推定:
  推定最小値 0.2500
  推定最大値 1.3611
推定スケーリング:
  λ_min = a * 推定最小 + b * 推定最大
  λ_max = c * 推定最小 + d * 推定最大
  a = 0.0000
  b = 0.1000
  c = 0.0000
  d = 1.0000
```
