```
definePopulation(numFounders, endSize, numGenCha, numGenCon, numGenFinal, numInd, useWeights, usePedigree, pedFile, pedOutput);
```

シミュレーションのための集団構造を作成します。

この関数は異なる集団構造を生成し、ユーザー定義の系譜に従うオプションがあります。

# 引数

  * `numFounders`: 基本集団の創始者の数
  * `endSize`: changingPopSizeステップで最終的に得られる個体の数
  * `numInd`: シミュレーションされる個体の数
  * `numGenCha`: changingPopSize関数のための世代数
  * `numGenCon`: constantPopSize関数のための世代数
  * `numGenFinal`: 個体を選択するために使用される最終世代の数
  * `useWeights`: 最終集団構成における各寄与世代の重み
  * `usePedigree`: 系譜を使用しない場合はfalseに設定し、そうでない場合は使用する系譜ファイルを指定します
  * `pedFile`: 系譜ファイル
  * `pedOutput`: 系譜出力を返す場合はtrueに設定します

# 注意事項

  * 複雑な集団構造を定義する際には、定常集団と変化集団の組み合わせ（および複数の集団の組み合わせ）を変更することを検討してください。

# 例

```julia
julia> definePopulation(100, 500, 20, 100, 4, 96,  Array{Float64}(undef,0), false, "sim.ped", false);
```
