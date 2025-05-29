```
pastplates(; time=100, proj="", title="time", coastlines=true, fmt="png", name="", data=false, show=true)
```

指定された時間で過去のプレートの再構築をプロットします。データはGPLATES https://gws.gplates.org ウェブサイトから抽出されます。

# Kwargs

  * `time`: 時間（Ma単位）。デフォルトは100 Maです。
  * `proj`: `coast()`で使用されるような投影文字列。
  * `title`: プロットのタイトル
  * `coastlines`: 海岸線をプロットするかどうかを示すブール値。
  * `fmt`: プロットの形式（デフォルトは`png`）
  * `name`: プロットの名前。デフォルトの名前を使用する代わりに、名前を指定すると、その名前で図が保存されます。
  * `data`: trueの場合、`pastplates`はプロットする代わりに`GMTdataset`のベクトルの形でデータを返します。デフォルトは最小限の良いプロットを生成しますが、さらなる改善のためにデータをダウンロードして自分でプロットを作成してください。
  * `show`: trueの場合（デフォルト）、自動的にプロットを表示します（`data=true`の場合は無視されます）。

# 例

```julia
pastplates()
```
