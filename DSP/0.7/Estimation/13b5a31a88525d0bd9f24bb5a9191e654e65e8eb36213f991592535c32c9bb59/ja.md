```
esprit(x::AbstractArray, M::Integer, p::Integer, Fs::Real=1.0)
```

周波数推定のためのESPRIT [^Roy1986]アルゴリズム。回転不変技術による信号パラメータの推定

未知の周波数のp個の正弦波の合計である長さNの信号"x"が与えられたとき、p個の周波数の配列を推定して返します。

# 引数

  * `x::AbstractArray`: 複素数長さNの信号配列
  * `M::Integer`: 相関行列のサイズ、N以下でなければなりません。信号サブスペースは、N-M+1の信号行列のSVDから計算されます。これは、信号xの長さMのシフトのN-M+1の列から形成されます。1つの正弦波に対して最良のパフォーマンスを得るには、M = (N+1)/3を使用します（van der VeenとLeusによる）。より小さなSVDのために、より速い実行を得るには、小さなMまたは小さなN-Mを使用します。
  * `p::Integer`: 推定する正弦波の数。
  * `Fs::Float64`: サンプリング周波数（Hz単位）。

# 戻り値

Hz単位の周波数の長さpの実数配列。

[^Roy1986]: R Roy, A Paulraj and T Kailath, ESPRIT - A subspace approach to estimation of parameters of cisoids in noise, IEEE Trans. Acoustics, Speech, Signal Process., 34, 1340-1342 (1986). [url](http://ieeexplore.ieee.org/abstract/document/1164935/).
