```
sgl_2020_train(f::Union{String,Symbol} = "")
```

2020年SGLフライトデータ収集のフライトデータ - トレーニング部分。カナダのオンタリオ州オタワ近郊で2020年6月20日から2020年7月7日までSander Geophysics Ltd. (SGL)によってCessna Grand Caravanを使用して収集されました。含まれるファイル:

  * `Flt1002_train.h5`
  * `Flt1003_train.h5`
  * `Flt1004_train.h5`
  * `Flt1005_train.h5`
  * `Flt1006_train.h5`
  * `Flt1007_train.h5`

**引数:**

  * `f`: (オプション) データファイルの名前（`_train`および`.h5`拡張子はオプション）

**戻り値:**

  * `p`: フォルダのパスまたは`f`データファイル
