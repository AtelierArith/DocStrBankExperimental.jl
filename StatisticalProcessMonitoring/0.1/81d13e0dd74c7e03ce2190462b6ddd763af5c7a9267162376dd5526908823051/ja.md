```
saCL(CH::ControlChart[; rlsim::Function, kw...])
```

制御チャートオブジェクト `CH` を変更することなく、Capizzi と Masarotto (2016) の確率的近似アルゴリズムを適用します。

### キーワード引数

アルゴリズムおよびキーワード引数に関する詳細は `saCL!` のドキュメントを参照してください。

### 戻り値

  * 推定された制御限界 `h`、総反復回数 `iter`、およびアルゴリズムの収束に関する情報 `status` を含む `NamedTuple`。

### 参考文献

  * Capizzi, G., & Masarotto, G. (2016). "Efficient Control Chart Calibration by Simulated Stochastic Approximation". IIE Transactions 48 (1). https://doi.org/10.1080/0740817X.2015.1055392.

```
