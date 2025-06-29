```
resample(d::RheoTimeData [, t, dt, scale )
```

データを1Dスプライン外挿を使用して再サンプリングします（Dierckx.jlパッケージを使用）。

# 引数

  * `d`: ストレスおよび/またはひずみを含む時間を持つ`RheoTimeData`構造体としてのデータ。追加のパラメータがない場合、データは一定の時間点数で均一なサンプリングを提供するように再サンプリングされます。
  * `t`: データが提供される時間点を決定する配列または範囲。
  * `dt`: 配列`t`が提供されていない場合、パラメータ`dt`はデータの均一な再サンプリングのためのタイムステップを設定します。
  * `scale`: 特定の時間点やタイムステップを指定する代わりに、サンプリングレートに対する全体的な乗数を提供できます。これはダウンサンプリング（`scale`<1）またはアップサンプリング（`scale`>1）を行うことができます。タイムステップが非均一な場合、値はそれに応じて補間されます。

# 例

`d`が`RheoTimeData`データセットであると仮定します：

  * `resample(d)`はサンプリングポイントの数を同じに保ちながら、均一なタイムステップを設定するために補間します。
  * `resample(d, t=-1:0.1:10)`は補間によって再サンプリングし、範囲`t`によって与えられた時間点を持つ新しいデータセットを生成します。
  * `resample(d, dt=0.1)`は補間によって再サンプリングし、均一なタイムステップ`dt`を持つ新しいデータセットを生成します。
  * `resample(d, scale=2)`はサンプリングレートを2倍にして再サンプリングします。
