```
rainfarm(r,slope,nf,weight=1.;fglob=false, fsmooth=false, verbose=false)
```

一般的なRainFARMダウンスケーリングを実行します。

# 引数

  * `r`      : ダウンスケールする大規模配列
  * `slope`  : 空間スペクトルスロープ
  * `nf`     : 空間ダウンスケーリングの精緻化係数
  * `weight` : 地形ダウンスケーリングのための重み
  * `fglob`  : ドメイン全体のグローバル平均を保存
  * `fsmooth`: gp保存の代わりにスムージングを使用
  * `verbose`: 進捗報告を提供
