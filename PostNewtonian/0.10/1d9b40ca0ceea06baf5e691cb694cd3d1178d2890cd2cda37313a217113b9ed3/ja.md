```
tidal_heating(pnsystem)
```

バイナリ内の各ブラックホールへのエネルギーおよび角運動量吸収率を計算します。

返される量はタプル `(Ṡ₁, Ṁ₁, Ṡ₂, Ṁ₂)` で、ブラックホール1およびブラックホール2のスピン（大きさ）と質量の変化率を表します。これらは一般的な — おそらく歳差運動する — 非離心バイナリに適用されます。この用語の集まりは [Alvi (2001)](https://doi.org/10.1103/PhysRevD.64.104020) から来ています。離心系に対するAlviの分析を拡張するのはそれほど難しくないでしょう。

結果の有効性は、PNパラメータ $v$ のみならず、スピンの角度が分離ベクトル $n̂$ に対してどのようであるかにも依存します：角度が小さいほど、近似が破綻することが予想される $v$ は低くなります。

関連文献

  * [Tagoshi and Sasaki (1994)](http://arxiv.org/abs/gr-qc/9405062)
  * [Poisson and Sasaki (1995)](https://arxiv.org/abs/gr-qc/9412027)
  * [Tagoshi et al. (1997)](https://arxiv.org/abs/gr-qc/9711072)
  * [Porto (2007)](https://arxiv.org/abs/0710.5150)
  * [Chatziioannou et al. (2012)](https://arxiv.org/abs/1211.1686)

この関数で使用されるホライズン量の計算に関する詳細については、["Horizons"](@ref Horizons) のドキュメントセクションを参照してください。
