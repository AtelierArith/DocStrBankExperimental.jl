# 集団遺伝学シミュレーション

リポジトリ:    https://www.github.com/pdimens/PopGenSims.jl/ ドキュメント: https://biojulia.net/PopGen.jl/

始めるためにできるいくつかのこと:

## PopGenCoreを使用してデータをインポート

  * `PopGenCore.read(filename; kwargs...)`
  * `genepop(infile; kwargs...)`  または類似のファイル特有のインポータ
  * 利用可能な `@gulfsharks` または `@nancycats` データセットを使用

## 集団内のサンプルをシミュレート

  * `simulate(popdata, n = 100)` を使用して集団特有のアレル頻度を用いてサンプルをシミュレート

## 交配交差をシミュレート

  * `cross(popdata, parent1, parent2, ...)` を使用して同じPopDataから2つの親を交配
  * `cross(popdata => parent1, popdata => parent2, ...)` を使用して異なるPopDataから2つの親を交配（例: バッククロス）

## 兄弟関係をシミュレート

  * `simulatekin(popdata, fullsib = , halfsib = , unrelated = , ...)` を使用して既知の親族関係を持つ個体のペアを生成する交配イベントをシミュレート。
