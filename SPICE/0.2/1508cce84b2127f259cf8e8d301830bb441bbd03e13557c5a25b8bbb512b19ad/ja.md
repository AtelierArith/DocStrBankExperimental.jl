```
spkpvn(handle, descr, et)
```

指定されたSPKセグメントと時間に対して、セグメントのターゲット天体の運動中心に対する状態（位置と速度）を返します。

### 引数

  * `handle`: ファイルハンドル
  * `descr`: セグメント記述子
  * `et`: 評価エポック

### 出力

  * `ref`: セグメント参照フレームIDコード
  * `state`: 出力状態ベクトル
  * `center`: 状態の中心

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/spkpvn_c.html)

```
