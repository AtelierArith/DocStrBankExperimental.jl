# ジュリアにおける集団遺伝学の分析

リポジトリ:    https://www.github.com/biojulia/PopGen.jl/ ドキュメント: https://biojulia.dev/PopGen.jl/

始めるためにできるいくつかのこと:

## データのインポート

  * `PopGen.read(filename, kwargs...)`
  * `genepop(infile, kwargs...)`  または類似のファイル特有のインポータ
  * 利用可能な `@gulfsharks` または `@nancycats` データセットを使用

## PopDataの探索

  * `populations(PopData)` で集団情報を表示
  * `loci(PopData)` でローカス名を表示
  * `samplenames(PopData)` でサンプル名を表示
  * `missingdata(PopData, by = ...)` で欠損情報を表示

## PopDataの操作

  * `populations!(PopData, ...)` で集団の名前を変更
  * `locations!(PopData, ...)` で地理的座標を追加
  * `exclude!(PopData, kwargs...)` でデータを選択的に削除

## 分析

  * `richness(PopData)` でアレルの豊富さを計算
  * `Kinship(PopData, method = ...)` で個体のペアワイズの親族関係を取得
  * `summary(PopData)` でF統計量、ヘテロ接合性などを計算
  * `hwetest(PopData)` でハーディー・ワインバーグ平衡をテスト
  * `pairwisefst(PopData)` で集団ペア間のFSTを計算
  * `cluster(PopData, kmeans, k = 3)` でKmeans++クラスタリングを実行
