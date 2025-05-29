```
combinedCL(CH::ControlChart; kw...)
```

制御チャートオブジェクト `CH` を変更することなく、制御チャートの制御限界を見つけるために二分法アルゴリズムを適用します。二分法アルゴリズムのための制御限界の上限 `hmax` は、Capizzi と Masarotto (2016) の確率近似アルゴリズムを使用して見つけられます。アルゴリズムとキーワード引数に関する詳細は `combinedCL!` のドキュメントを参照してください。

### キーワード引数

  * キーワード引数のリストについては `combinedCL!` のドキュメントを参照してください。

### 戻り値

  * 推定された制御限界 `h`、総反復回数 `iter`、およびアルゴリズムの収束に関する情報 `status` を含む `NamedTuple`。

### 参考文献

  * Qiu, P. (2013). Introduction to Statistical Process Control. Boca Raton: CRC Press.
  * Capizzi, G., & Masarotto, G. (2016). Efficient control chart calibration by simulated stochastic approximation. IIE Transactions, 48(1), 57-65. https://doi.org/10.1080/0740817X.2015.1055392
