```
mcpc3ds_meepi(phase, mag; TEs, keyargs...)

mcpc3ds_meepi(compl; TEs, keyargs...)

mcpc3ds_meepi(phase; TEs, keyargs...)
```

5D MEEPI（マルチエコー、マルチタイムポイント）入力に対してMCPC-3D-S位相オフセット除去を実行します。位相オフセットはテンプレートタイムポイントのために計算され、すべてのボリュームから除去されます。

## オプションのキーワード引数

  * `echoes`: 定義されたエコーのみを使用します。デフォルト: `echoes=[1,2]`
  * `sigma`: 位相オフセットの平滑化パラメータ。デフォルト: `sigma=[10,10,5]`
  * `po`: 位相オフセットはこの配列に格納されます。位相オフセットを取得したり、メモリマッピングで作業するために使用できます。
  * `template_tp`: テンプレート計算のためのタイムポイント。デフォルト: `template_tp=1`
