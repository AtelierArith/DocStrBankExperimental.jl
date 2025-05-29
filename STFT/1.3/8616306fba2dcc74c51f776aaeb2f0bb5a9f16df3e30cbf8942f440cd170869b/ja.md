```
synthesis(X::Matrix, w::Vector, L=0, N=length(w)) -> Vector

istft(X::Matrix, w::Vector, L=0, N=length(w)) -> Vector
```

STFT領域の信号$Y_w[sH, n]$から離散時間領域の信号$y[n]$を合成します。任意のSTFT領域の信号$Y_w[sH, n]$は、一般に、$Y_w[sH, n]$のSTFTが与えられる離散時間領域の信号が存在しないため、有効なSTFTではありません[1]。その結果、時間領域の信号は次の式を使用して推定する必要があります[1]:

$$
y[n] = \frac{
    \sum\limits_{s=-\infty}^{+\infty} w[n - sH] \ y_w[sH, n]
}{
    \sum\limits_{s=-\infty}^{+\infty} w^2[n - sH]
},
$$

ここで、$w[n]$は分析ウィンドウの時間領域信号、$y_w[sH, n]$は$Y_w[sH, n]$の時間領域表現、$H$は2つの連続する信号セグメント間のサンプル数を決定する非負整数値（`hop`としても知られる）です。

# パラメータ

  * `X` - 離散STFT領域信号のサンプルを含む行列。
  * `w` - 離散時間領域の分析ウィンドウのサンプルを含む配列。
  * `L` - 2つの連続するセグメント間のサンプルのオーバーラップ。デフォルト値は`0`です。
  * `N` - 逆DFT計算に使用される離散周波数ビンの数。デフォルト値は`length(w)`です。`N < length(w)`の場合、情報の損失を避けるために`N=length(w)`が強制されます。

# 戻り値

  * `x` - 推定された時間領域信号を含む実数ベクトル。

# 注意

1. $$
    H
    $$

    と$L$の関係は$H = W - L$として与えられ、ここで$W$はウィンドウの長さです。
2. この関数は、片側STFT領域信号からの実数値信号の合成のみをサポートします。
3. 合成された時間領域信号は、全体のセグメントのみが分析されるため、分析された信号よりも短くなる可能性があります。

# 例

```julia
import STFT

x = rand(100)   # モック信号を生成
W = 64          # ウィンドウの長さ
w = ones(W)     # 長方形の分析ウィンドウ
H = 4           # ホップ
L = W - H       # オーバーラップ

X  = STFT.analysis(x, w, L)  # 分析
xr = STFT.synthesis(X, w, L) # 合成
```

```julia
using STFT

x = rand(100)   # モック信号を生成
W = 64          # ウィンドウの長さ
w = ones(W)     # 長方形の分析ウィンドウ
H = 4           # ホップ
L = W - H       # オーバーラップ

X  = stft(x, w, L)  # 分析
xr = istft(X, w, L) # 合成
```

# 参考文献

1. D. Griffin and J. Lim, “Signal estimation from modified short-time Fourier transform,” IEEE Transactions on Acoustics, Speech, and Signal Processing, vol. 32, no. 2, pp. 236–243, Apr. 1984, doi: 10.1109/TASSP.1984.1164317. [[IEEE Xplore](https://ieeexplore.ieee.org/abstract/document/1164317)]

```
