```
descriptives(data, vars, sort = nothing; kwargs...)
```

  * kwargs:
  * `skipmissing` - NaNおよびMissing値を削除、デフォルト = true;
  * `skipnonpositive` - "log-statistics"のために非正の値（およびNaN、Missing）を削除 - :geom, :geomean, :logmean, :logvar, :geocv;
  * `stats` - デフォルトで`stats = [:n, :mean, :sd, :se, :median, :min, :max]`に設定;
  * `corrected` - 補正された分散を使用（true）;
  * `level` - 信頼区間のレベル（0.95);

`stats`の可能な値は次のとおりです:

  * :n - 観測数;
  * :posn - 正の（非負の）観測数;
  * :mean - 算術平均;
  * :var - 分散;
  * :bvar - 補正なしの分散;
  * :geom - 幾何平均;
  * :logmean - 対数変換データの算術平均;
  * :logvar - 対数変換データの分散 $σ^2_{log}$;
  * :sd - 標準偏差（またはσ）;
  * :se - 標準誤差;
  * :cv - 変動係数;
  * :geocv - 対数変換データの変動係数 ($CV = sqrt{exp(σ^2_{log})-1}$);
  * :lci - 下側信頼区間;
  * :uci - 上側信頼区間;
  * :lmeanci - 平均の下側信頼区間;
  * :umeanci - 平均の下側信頼区間;
  * :median - 中央値;
  * :min - 最小値;
  * :max - 最大値;
  * :range - 範囲;
  * :q1 - 下四分位数;
  * :q3 - 上四分位数;
  * :iqr - 四分位範囲;
  * :kurt - 尖度;
  * :skew - 歪度;
  * :harmmean - 調和平均;
  * :ses - 歪度の標準誤差;
  * :sek - 尖度の標準誤差;
  * :sum - 合計.
