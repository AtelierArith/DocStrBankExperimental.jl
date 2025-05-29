```
FDFilterIF(sys; mu = 0, md = 0, mf = 0, mw = 0, ma = 0, moff = 0) -> R::FDFilterIF
```

与えられた線形時間不変の記述子システムモデル `sys = (A-λE,B,C,D)` に対して、FDIフィルタの合成関数によって決定される故障検出フィルタ内部形式オブジェクト `R` を構築します。 `mu`、`md`、`mf`、`mw` および `maux` は、それぞれ制御、外乱、故障、ノイズおよび補助入力ベクトルの次元です。 `B = [Boff Bu Bd Bf Bw Bv]` および `D = [Doff Du Dd Df Dw Dv]` は、`Boff` と `Doff` が `moff` 列、`Bu` と `Du` が `mu` 列、`Bd` と `Dd` が `md` 列、`Bf` と `Df` が `mf` 列、`Bw` と `Dw` が `mw` 列、`Bv` と `Dv` が `maux` 列を持つように分割された行列です。

結果として得られる `R` には、分割されたシステム `R.sys = (A-λE,[Bu Bd Bf Bw Bv],C,[Du Dd Df Dw Dv])` が含まれ、制御、外乱、故障、ノイズおよび補助入力ベクトルの次元はそれぞれ `R.mu`、`R.md`、`R.mf`、`R.mw` および `R.ma` に含まれます。
