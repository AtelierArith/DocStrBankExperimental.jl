```
FDIFilterIF(sys; mu = 0, md = 0, mf = 0, mw = 0, ma = 0, moff = 0 ) -> R::FDIFilterIF
```

線形時間不変記述子システムモデルのベクトル `sys[i] = (Ai-λEi,Bi,Ci,Di)` に対して、FDIフィルタの合成関数によって決定される故障検出および隔離フィルタ内部形式オブジェクト `R` を構築します。 `mu`、`md`、`mf`、`mw` および `ma` は、それぞれ制御、外乱、故障、ノイズおよび補助入力ベクトルの次元です。 各 `Bi = [Boffi Bui Bdi Bfi Bwi Bvi]` および `Di = [Doffi Dui Ddi Dfi Dwi Dvi]` は、`Boffi` および `Doffi` が `moff` 列、`Bui` および `Dui` が `mu` 列、`Bdi` および `Ddi` が `md` 列、`Bfi` および `Dfi` が `mf` 列、`Bwi` および `Dwi` が `mw` 列、`Bvi` および `Dvi` が `ma` 列を持つように分割された行列と仮定します。

結果として得られる `R` には、分割されたシステムのベクトル `R.sys[i] = (A-λE,[Bui Bdi Bfi Bwi Bvi],C,[Dui Ddi Dfi Dwi Dvi])` が含まれ、制御、外乱、故障、ノイズおよび補助入力ベクトルの次元はそれぞれ `R.mu`、`R.md`、`R.mf`、`R.mw` および `R.ma` に含まれます。  
