```
bisectionCL(CH::ControlChart, hmax; kw...)
```

制御チャートオブジェクト `CH` を変更することなく、制御限界を見つけるために二分法アルゴリズムを適用します。

### キーワード引数

アルゴリズムとキーワード引数に関する詳細は `bisectionCL!` のドキュメントを参照してください。

### 戻り値

  * 推定された制御限界 `h`、総反復回数 `iter`、およびアルゴリズムの収束に関する情報 `status` を含む `NamedTuple`。

### 参考文献

  * Qiu, P. (2013). Introduction to Statistical Process Control. Boca Raton: CRC Press.

```
