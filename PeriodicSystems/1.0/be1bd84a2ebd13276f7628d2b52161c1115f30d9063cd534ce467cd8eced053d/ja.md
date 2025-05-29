```
 pszero(psys::PeriodicStateSpace{PeriodicMatrix}[, K]; atol, rtol, fast) -> val
 pszero(psys::PeriodicStateSpace{PeriodicArray}[, K]; atol, rtol, fast) -> val
```

離散時間周期システム `psys = (A(t), B(t), C(t), D(t))` の有限および無限のゼロを `val` に計算します。ここで、周期システム行列 `A(t)`, `B(t)`, `C(t)`, `D(t)` は *Periodic Matrix* または *Periodic Array* 表現のいずれかです。オプションの引数 `K` は、周期行列のシーケンスを開始するための希望の時間を指定します（デフォルト: `K = 1`）。

ゼロの計算は、無限および有限のゼロと左および右のクロンカー指数を含む行列ペンシル `M-λN` の分離を行う *fast* 構造に依存しています。削減は直交類似変換を使用して行われ、`fast = true` の場合は列ピボッティングを伴うランクを明らかにするQR分解に基づくランク決定を含み、`fast = false` の場合は、より信頼性の高いSVD分解を使用します。

キーワード引数 `atol` と `rtol` は、それぞれ周期システム行列の非ゼロ要素に対する絶対および相対許容誤差を指定します。デフォルトの相対許容誤差は `n*ϵ` であり、ここで `n` は周期行列の最大次元に比例し、`ϵ` は作業用マシンエプシロンです。

*参考文献*

[1] A. Varga and P. Van Dooren. Computing the zeros of periodic descriptor systems.     Systems & Control Letters 50:371–381, 2003.
