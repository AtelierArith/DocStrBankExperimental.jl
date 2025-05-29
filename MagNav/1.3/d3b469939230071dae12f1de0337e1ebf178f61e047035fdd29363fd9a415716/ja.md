```
sgl_2021_train(f::Union{String,Symbol} = "")
```

2021年SGLフライトデータコレクションからのフライトデータ - トレーニング部分。カナダのオンタリオ州オタワ近郊で、Sander Geophysics Ltd. (SGL) によってCessna Grand Caravanを使用して2021年12月13日から2022年1月5日まで収集されました。含まれるファイル:

  * `Flt2001_train.h5`
  * `Flt2002_train.h5`
  * `Flt2004_train.h5`
  * `Flt2005_train.h5`
  * `Flt2006_train.h5`
  * `Flt2007_train.h5`
  * `Flt2008_train.h5`
  * `Flt2015_train.h5`
  * `Flt2016_train.h5`
  * `Flt2017_train.h5`

**引数:**

  * `f`: (オプション) データファイルの名前 (`_train` & `.h5` 拡張子はオプション)

**戻り値:**

  * `p`: フォルダのパスまたは `f` データファイル
