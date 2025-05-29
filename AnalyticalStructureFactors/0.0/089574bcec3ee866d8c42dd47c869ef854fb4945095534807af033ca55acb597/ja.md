```
betaU_Yukawa(amplitude::β_num, inv_screening_length::β_num, k::β_num) where {β_num<:AbstractFloat}
```

ユカワポテンシャルのフーリエ変換を計算するための補助関数で、β = 1/(k*B T*abs)で乗算されます。結果はβ * u*Yukawa*tilde(k)です。

実空間における無次元ユカワポテンシャルは、u(r/σ) = (Amplitude) * exp(-z*(r/σ - 1)) / (r/σ) であり、r/σ >= 1のときに成り立ちます。フーリエ変換は、正確な定義と正規化に応じてさまざまな形を取ることができます。ここで使用される式（ユーザーからのもの）は次のとおりです：βu_tilde(k) = Factor * Amplitude * (k*cos(k) + z*sin(k)) / (k*(k² + z²)) ここで、kはqσ、zはinv*screening*length、Factorは4πです。小さなkの展開は次のようになります：βu_tilde(k) ≈ Factor * Amplitude * ( (1/z) + 1 - (z²+9z+6)/(6z²) * k² )

注意：k -> 0の制限において、主な式と元のコードで提供された小kの展開との間に不一致があります。k->0の主な式は(1+z)/z²を与えますが、展開は(1+z)/zを与えます。この実装は、提供された式を使用します。

# 引数

  * `amplitude::β_num`: ユカワポテンシャルの有効振幅（しばしばβを含む、例：βε）。
  * `inv_screening_length::β_num`: 無次元逆スクリーン長（z）。
  * `k::β_num`: 無次元波ベクトル（k = q*σ）。

# 戻り値

  * `β_num`: β * u*Yukawa*tilde(k)の値。

# 参考文献

[1] Yukawa, H. (1935). "On the interaction of elementary particles". Proc. Phys.-Math. Soc. Jpn. 17: 48.     （注意：液体に対する特定の形はしばしばこれから導出されますが、異なる場合があります。）
