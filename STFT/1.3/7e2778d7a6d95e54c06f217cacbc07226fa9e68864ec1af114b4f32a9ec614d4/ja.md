```
analysis(x::Vector, w::Vector, L=0, N=length(w)) -> Matrix
analysis(x::Array{Vector}, w::Vector, L=0, N=length(w)) -> Array{Matrix}

stft(x::Vector, w::Vector, L=0, N=length(w)) -> Matrix
stft(x::Array{Vector}, w::Vector, L=0, N=length(w)) -> Array{Matrix}
```

離散時間領域信号 $\mathrm{x}[n]$ を短時間フーリエ変換を用いて分析します。これは次のように表されます。

$$
\mathrm{X}[sH, \omega] =
    \sum_{n = -\infty}^{+\infty}
        \mathrm{w}[n - sH] \ \mathrm{x}[n] e^{-j\omega n},
$$

ここで、$s$ と $\omega$ はそれぞれセグメントインデックスと角周波数を示し、$\mathrm{w}[n]$ は分析ウィンドウの離散時間領域信号であり、$H$ は2つの連続した信号セグメント間のサンプル数を決定する非負整数値（`hop`としても知られています）です。

# パラメータ

  * `x` - 離散時間領域信号のサンプルを含む配列。
  * `w` - 離散時間領域分析ウィンドウのサンプルを含む配列。
  * `L` - 2つの連続したセグメント間のサンプルのオーバーラップ。デフォルト値は `0` です。
  * `N` - DFT計算に使用される離散周波数ビンの数。デフォルト値は `length(w)` です。`N < length(w)` の場合、情報の損失を避けるために `N=length(w)` が強制されます。

# 戻り値

  * `X` - STFT領域信号を含む複素行列。

# 注意

1. $$
    H
    $$

    と $L$ の関係は $H = W - L$ で与えられ、ここで $W$ はウィンドウの長さです。
2. 実数値（`x isa Real`）の入力信号の場合、関数はサイズが `(N÷2+1, S)` の行列を返します。ここで、$S$ はセグメントの数です；すなわち、片側スペクトルです。
3. 複素値（`x isa Complex`）の入力信号の場合、関数はサイズが `(N, S)` の行列を返します。ここで、$S$ はセグメントの数です；すなわち、両側スペクトルです。

# 例

```julia
import STFT

x = rand(10000) # モック信号を生成
W = 64          # ウィンドウの長さ
w = ones(W)     # 長方形分析ウィンドウ
H = 10          # ホップ
L = W - H       # オーバーラップ

X = STFT.analysis(x, w, L)  # 分析
```

```julia
using STFT

x = rand(100)   # モック信号を生成
W = 64          # ウィンドウの長さ
w = ones(W)     # 長方形分析ウィンドウ
H = 4           # ホップ
L = W - H       # オーバーラップ

X  = stft(x, w, L)  # 分析
```
