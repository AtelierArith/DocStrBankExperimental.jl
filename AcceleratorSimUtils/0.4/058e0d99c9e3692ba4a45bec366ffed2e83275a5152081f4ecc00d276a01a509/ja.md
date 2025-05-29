function gen_pinknoise(     beta::Float64=1.0, size::Int64=2^12, dt::Float64=1.0, f0::Float64=1.0)

周波数ロールオフ係数 `beta` を持つ「ピンクノイズ」スペクトルの乱数生成器。

## 位置パラメータ:

  * beta             – 型:Float64, 周波数ロールオフ係数
  * size             – 型:Int64, ポイント数

## キーワードパラメータ:

  * dt               – 型:Float64, 各データ間の差, 合計時間 = size * dt, 単位: s
  * f0               – 型:Float64, スペクトルは形状 (f0/f)^(beta) を持つ, 単位: Hz.

注: アルゴリズムは "Timmer, J. and Koenig, M.: On generating power law noise. Astron. Astrophys. 300, 707-710 (1995)" に基づいています。
