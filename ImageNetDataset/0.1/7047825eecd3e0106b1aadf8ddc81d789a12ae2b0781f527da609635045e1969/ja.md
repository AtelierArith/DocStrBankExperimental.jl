```
ImageNet(; split=:train, dir=nothing, kwargs...)
ImageNet([split])
```

ImageNet 2012分類データセット（ILSVRC 2012-2017）。

これはImageNetの中で最も広く使用されているサブセットです。1000のオブジェクトクラスを網羅し、1,281,167のトレーニング画像、50,000の検証画像、100,000のテスト画像を含んでいます。デフォルトでは、各画像はRGBカラースペースの`224 × 224 × 3`形式です。これは前処理器`transform`を変更することで変更できます。

# 引数

  * データセットをロードまたはダウンロードする特定の`dir`を渡すことができます。そうでなければ、デフォルトのものを使用します。
  * `train_dir`、`val_dir`、`test_dir`、`devkit_dir`：`dir`のオプションのサブディレクトリ名。デフォルトは`"train"`、`"val"`、`"test"`、`"devkit"`です。
  * `split`：データパーティションを選択します。`:train:`、`:val`、`:test`の値を取ることができます。デフォルトは`:train`です。
  * `transform`：画像ファイルを配列に変換するために適用される前処理器。入力としてファイルパスを想定し、出力としてWHC形式の配列を生成します。デフォルトは[`CenterCropNormalize`](@ref)で、中心クロッピングビューを適用し、PyTorchのビジョンモデルからの係数を使用して正規化します。

# フィールド

  * `split`：選択されたデータパーティションを示すシンボル
  * `transform`：前処理パイプライン。出力の次元とタイプを選択するように構成できます。
  * `paths`：ImageNet画像へのパス
  * `targets`：教師あり学習のためのターゲットを格納する配列。
  * `metadata`：データセットに関する追加情報を含む辞書。

また、[`AbstractTransform`](@ref)、[`CenterCropNormalize`](@ref)も参照してください。

# メソッド

  * `dataset[i]`：観測値`i`を特徴とターゲットの名前付きタプルとして返します。
  * `dataset[:]`：すべての観測値を特徴とターゲットの名前付きタプルとして返します。
  * `length(dataset)`：観測値の数。
  * [`convert2image`](@ref)は特徴を`RGB`画像に変換します。

# 例

```julia-repl
julia> using ImageNetDataset

julia> dataset = ImageNet(:val);

julia> dataset[1:5].targets
5-element Vector{Int64}:
 1
 1
 1
 1
 1

julia> X, y = dataset[1:5];

julia> size(X)
(224, 224, 3, 5)

julia> X, y = dataset[2000];

julia> convert2image(dataset, X)

julia> dataset.metadata
Dict{String, Any} with 4 entries:
  "class_WNIDs"       => ["n01440764", "n01443537", "n01484850", "n01491361", "n01494475", …
  "class_description" => ["freshwater dace-like game fish of Europe and western Asia noted …
  "class_names"       => Vector{SubString{String}}[["tench", "Tinca tinca"], ["goldfish", "…
  "wnid_to_label"     => Dict("n07693725"=>932, "n03775546"=>660, "n01689811"=>45, "n021008…

julia> dataset.metadata["class_names"][y]
  3-element Vector{SubString{String}}:
   "common iguana"
   "iguana"
   "Iguana iguana"
```

# 参考文献

[1]: [Russakovsky et al., ImageNet Large Scale Visual Recognition Challenge](https://arxiv.org/abs/1409.0575)
