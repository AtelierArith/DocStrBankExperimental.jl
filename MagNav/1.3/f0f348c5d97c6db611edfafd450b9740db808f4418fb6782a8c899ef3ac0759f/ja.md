```
xyz2h5(xyz_xyz::String, xyz_h5::String, flight::Symbol;
       lines::Vector        = [()],
       lines_type::Symbol   = :exclude,
       tt_sort::Bool        = true,
       downsample_160::Bool = true,
       return_data::Bool    = false)
```

SGLフライトデータファイルを.xyzからHDF5に変換します。

  * SGLフライトに対して有効:

      * `:Flt1001`
      * `:Flt1002`
      * `:Flt1003`
      * `:Flt1004_1005`
      * `:Flt1004`
      * `:Flt1005`
      * `:Flt1006`
      * `:Flt1007`
      * `:Flt1008`
      * `:Flt1009`
      * `:Flt1001_160Hz`
      * `:Flt1002_160Hz`
      * `:Flt2001_2017`

1GB以上のファイルには1時間以上かかる場合があります。参考までに、1.23GBのファイルは64GBのMacBook Proを使用して46.8分で処理されました。

**引数:**

  * `xyz_xyz`:        フライトデータの.xyzファイルのパス/名前（`.xyz`拡張子はオプション）
  * `xyz_h5`:         保存するフライトデータHDF5ファイルのパス/名前（`.h5`拡張子はオプション）
  * `flight`:         フライト名（例: `:Flt1001`）
  * `lines`:          （オプション）含めるまたは除外する選択された行番号、3要素のタプル（`line`,`start_time`,`end_time`）のベクターでなければなりません
  * `lines_type`:     （オプション）`lines`をONLY `:include`（すなわち、テストデータを生成するため）または`exclude`（すなわち、トレーニングデータを生成するため）するかどうか
  * `tt_sort`:        （オプション）trueの場合、データを時間でソートします（行ではなく）
  * `downsample_160`: （オプション）trueの場合、160Hzデータを10Hzにダウンサンプリングします（160Hzデータファイルのみ）
  * `return_data`:    （オプション）trueの場合、`xyz_h5`を作成する代わりに`data`を返します

**戻り値:**

  * `data`: `return_data = true`の場合、内部データ行列
