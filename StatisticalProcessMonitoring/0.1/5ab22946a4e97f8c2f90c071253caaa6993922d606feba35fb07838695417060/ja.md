```
bootstrapCL(CH::ControlChart; kw...)
```

シミュレートされたラン長パスに対して二分法アルゴリズムを適用し、制御チャートオブジェクト `CH` を変更することなく制御限界を見つけます。

### キーワード引数

アルゴリズムとキーワード引数に関する詳細は `bootstrapCL!` のドキュメントを参照してください。

### 戻り値

  * 推定された制御限界 `h`、総反復回数 `iter`、およびアルゴリズムの収束に関する情報 `status` を含む `NamedTuple`。

### 参考文献

  * Qiu, P. (2013). Introduction to Statistical Process Control. Boca Raton: CRC Press.
