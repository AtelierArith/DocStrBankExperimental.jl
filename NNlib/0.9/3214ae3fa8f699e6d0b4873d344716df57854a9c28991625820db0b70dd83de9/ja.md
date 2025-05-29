```
stft(x;
    n_fft::Int, hop_length::Int = n_fft ÷ 4, window = nothing,
    center::Bool = true, normalized::Bool = false,
)
```

短時間フーリエ変換 (STFT)。

STFTは、入力の短い重なり合ったウィンドウのフーリエ変換を計算し、信号の周波数成分が時間とともにどのように変化するかを示します。

$$
Y[\omega, m] = \sum_{k = 0}^{N - 1} \text{window}[k] \text{input}[m \times \text{hop length} + k] \exp(-j \frac{2 \pi \omega k}{\text{n fft}})
$$

ここで、$N$はウィンドウの長さ、$\omega$は周波数 $0 \le \omega < \text{n fft}$、$m$はスライディングウィンドウのインデックスです。

# 引数:

  * `x`: 入力は、1Dの時間系列（`(L,)` 形状）または2Dの時間系列のバッチ（`(L, B)` 形状）でなければなりません。

# キーワード引数:

  * `n_fft::Int`: フーリエ変換のサイズ。
  * `hop_length::Int`: 隣接するスライディングウィンドウフレーム間の距離。
  * `window`: 適用するオプションのウィンドウ関数。1Dベクトル `0 < length(window) ≤ n_fft` でなければなりません。ウィンドウが `n_fft` より短い場合、両側にゼロでパディングされます。`nothing`（デフォルト）の場合、ウィンドウは適用されません。
  * `center::Bool`: 入力を両側にパディングして、$t$-thフレームが時間 $t \times \text{hop length}$ に中心を置くかどうか。パディングは `pad_reflect` 関数で行われます。
  * `normalized::Bool`: 正規化されたSTFTを返すかどうか、すなわち $\text{n fft}^{-0.5}$ で乗算されます。

# 戻り値:

形状 `(n_fft, n_frames, B)` の複素数配列。ここで、`B` はオプションのバッチ次元です。
