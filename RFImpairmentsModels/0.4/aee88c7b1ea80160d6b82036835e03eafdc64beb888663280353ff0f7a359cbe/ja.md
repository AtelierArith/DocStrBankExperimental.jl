非線形PAモデルを、指定された`model`と関連するパラメータに基づいてインスタンス化します。

# Rapp PAモデル [:Rapp]

最初のモデルはRappモデル[1]で、特定の`backOff`パワーと`smoothness`パラメータ（膝パラメータとも呼ばれる）の関数です。Rapp非線形パワーアンプモデルはAM/AM歪みモデルのみであり、位相には影響を与えません。また、理論的な入力パワー値（すなわちE[|x[n]|²]）を指定することも可能です。実際、飽和は入力平均パワーに対するバックオフとして定義されます。パワーが指定されていない場合、推定パワーは時間系列から最初に計算されます（1/N ∑ | x[n]|²）。これは、強いピーク対平均パワー比を持つ信号に対してバイアスを引き起こす可能性があります。この場合、理論的なパワーを最初に計算し（この関数に`power`キーワードで渡す）一定の飽和値を得ることが有用です。   [1] = C. Rapp. Effects of HPA-nonlinearity on a 4-DPSK/OFDM-signal for a digital sound broadcasting signal. In P. S. Weltevreden, editor, ESA Special Publication, volume 332 of ESA Special Publication, Oct. 1991.

# Salehモデル

2番目のモデルはSalehモデルで、AM/AM歪みとAM/PM歪みの両方に影響を与えます。このモデルは4つのパラメータα*AM、β*AM、α*PM、β*PMによってパラメータ化されています。   [2] = A. A. M. Saleh. Frequency-independent and frequency-dependent nonlinear models of TWT amplifiers. 29(11):1715–1720.

# Ghorbaniモデル

3番目のモデルはGhorbaniモデルで、8つのパラメータ（a1、a2、a3、a4は振幅用、b1、b2、b3、b4は位相歪み用）を通じてAM/AM歪みとAM/PM歪みを定義します。

[3] = A. Ghorbani and M. Sheikhan. The effect of solid state power amplifiers (SSPAs) nonlinearities on MPSK and M-QAM signal transmission. In Digital Processing of Signals in Communications, 1991., Sixth International Conference On, pages 193–197

# ノンモデル

純粋な線形増幅で、障害が適用されていないことを確認するのに役立ちます。

initNonLinearPA(:Rapp;power=-1,backOff=0,smoothness=0)

  * power     : Rappモデル用。一定の飽和レベルのための理論的パワー。-1の場合、経験的パワーが使用されます（デフォルトは-1）

      * backOff   : Rappモデル用。バックオフ値、dB単位（デフォルトは0）
      * smoothness: Rappモデル用。スムーズネス値（通常1から10の間）（デフォルトは0）
      * α_AM      : Salehモデル用。AM歪みのためのαパラメータ（デフォルトは0）
      * β_AM      : Salehモデル用。AM歪みのためのβパラメータ（デフォルトは0）
      * α_PM      : Salehモデル用。PM歪みのためのαパラメータ（デフォルトは0）
      * β_PM      : Salehモデル用。PM歪みのためのβパラメータ（デフォルトは0）
      * a1,a2,a3,a4 : Ghorbaniモデル用。AM/AM歪みのためのパラメータ（デフォルトはすべて0）
      * b1,b2,b3,b4 : Ghorbaniモデル用。AM/PM歪みのためのパラメータ（デフォルトはすべて0）
      * linearGain : 線形PAモデル用。適用されるゲイン（デフォルトは1）
