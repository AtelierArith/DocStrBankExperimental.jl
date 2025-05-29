```
load_model(data, r, rmean, fittedparam, fixedeffects, transitions, G, R, S, insertstep, splicetype, nalleles, priorcv, onstates, decayrate, propcv, probfn, noisepriors, method, hierarchical, coupling, grid, zeromedian, ejectnumber, factor)
```

与えられたデータとオプションに対して適切なモデル構造体を構築して返します。

# 引数

  * `data`: データ構造。
  * `r`, `rmean`, `fittedparam`, `fixedeffects`, `transitions`, `G`, `R`, `S`, `insertstep`, `splicetype`, `nalleles`, `priorcv`, `onstates`, `decayrate`, `propcv`, `probfn`, `noisepriors`, `method`, `hierarchical`, `coupling`, `grid`, `zeromedian`, `ejectnumber`, `factor`: モデルオプション。

# 戻り値

  * モデル構造体（例: `GMmodel`, `GRSMmodel`）。
