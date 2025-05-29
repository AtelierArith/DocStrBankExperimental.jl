```
Rd = c2d(Rc, Ts, meth = "zoh"; prewarp_freq = freq, atol = 0, rtol = n*ϵ)
```

連続時間の有理伝達関数行列 `Rc` とサンプリング時間 `Ts` に対して、選択された離散化手法 `meth` に従って対応する離散化された有理伝達関数行列 `Rd` を計算します。

以下の離散化手法は、`meth` を適切に選択することで実行できます：

```
  "zoh"     - 入力のゼロ次保持（デフォルト）;

  "foh"     - 入力の線形補間（一次保持とも呼ばれる）;

  "impulse" - インパルス不変離散化;

  "matched" - 一致した極-零法（[1]を参照）;

  "Tustin"  - タスティン変換（台形積分とも呼ばれる）：非ゼロの前方周波数
              `freq` はキーワードパラメータ `prewarp_freq = freq` を使用して指定でき、
              `Rd(exp(im*freq*Ts)) = Rc(im*freq)` を保証します。
```

キーワード引数 `atol` と `rtol` は、それぞれ、`Rc` の要素の分子および分母多項式の非ゼロ係数に対する絶対および相対許容誤差を指定します。デフォルトの相対許容誤差は `10*ϵ` であり、ここで `ϵ` は作業用マシンエプシロンです。

*参考文献*：

[1] G.F. Franklin, D.J. Powell and M.L. Workman, Digital Control of Dynamic Systems (3rd Edition), Prentice Hall, 1997.
