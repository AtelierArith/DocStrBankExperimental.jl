```
yin(sig::Vector, sr::Int; kwargs...) -> F0s, frame_times
```

信号 `sig` の基本周波数 (F0) を YIN アルゴリズム [^1] を使用して推定します。信号 `sig` は、レート `sr` で均等にサンプリングされた点のベクトルです。

## キーワード引数

  * `w_len`: 分析ウィンドウのサイズ [サンプル == 点の数]
  * `f_step`: 2 つの連続したフレーム間のラグのサイズ [サンプル == 点の数]
  * `f0_min`: 検出可能な最小基本周波数 [線形周波数]
  * `f0_max`: 検出可能な最大基本周波数 [線形周波数]
  * `harmonic_threshold`: 検出の閾値。この閾値以下の CMNDF 関数の最初の最小値をアルゴリズムが返します。
  * `diffference_function`: 使用する差分関数 (デフォルトは `ChaosTools.difference_function_original`)。

## 説明

YIN アルゴリズム [^CheveigneYIN2002] は、信号の基本周波数 `F0` を、基本的に信号の自己相関を最小化する周期 `τ0` を探すことによって推定します。この自己相関は、長さ `w_len` の 2 つのウィンドウで構成される信号セグメント (フレーム) に対して計算されます。各ウィンドウは距離 `τ` で分離されており、各ウィンドウ間のペアワイズ差を最小化する距離が、そのフレームの基本周期 `τ0` と見なされます。

より正確には、アルゴリズムはまず、いくつかの候補周期 `τ` に対してフレームの 2 つのウィンドウ間の累積平均正規化差分関数 (MNDF) を計算します。候補周期は `τ_min=sr/f0_max` から `τ_max=sr/f0_min` までの範囲です。MNDF は次のように定義されます。

$$
d_t^\prime(\tau) = \begin{cases}
        1 & \text{if} ~ \tau=0 \\
        d_t(\tau)/\left[{(\frac 1 \tau) \sum_{j=1}^{\tau} d_{t}(j)}\right] & \text{otherwise}
        \end{cases}
$$

ここで `d_t` は差分関数です：

$$
d_t(\tau) = \sum_{j=1}^W (x_j - x_{j+\tau})^2
$$

次に、アルゴリズムは MNDF の局所最小値を放物線 (二次) 補間を使用して洗練します。これは、各最小値とその最初の隣接点を取り、対応する補間された放物線の最小値を見つけることによって行われます。MNDF の最小値は補間の最小値に置き換えられます。最後に、アルゴリズムは最小の周期を持ち、対応する MNDF が `harmonic threshold` 以下の最小値を選択します。これが存在しない場合、グローバル最小値に対応する周期を選択します。これは、最初の信号点から始まり、距離 `f_step` で分離されたフレームに対して繰り返されます (フレームは重複する可能性があります)。各フレームの周波数ベクトル `F0=sr/τ0` と各フレームの開始時間を返します。

注意として、周波数の物理単位は 1/[時間] であり、ここで [時間] はサンプリングレート `sr` によって決まります。たとえば、サンプリングレートが秒を超える場合、周波数はヘルツで表されます。

[^CheveigneYIN2002]: De Cheveigné, A., & Kawahara, H. (2002). YIN, a fundamental frequency estimator for

speech and music. The Journal of the Acoustical Society of America, 111(4), 1917-1930.
