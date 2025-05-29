```
makedata(Input::LogDiffInput, nSimulation::Integer)
```

は、提供された DataGenInput 構造体に従ってデータを生成します。

可能な DataGenInput タイプは次のとおりです。

  * `::LogDiffInput`
  * `::BootstrapInput{MovingBlock}`
  * `::BootstrapInput{CircularBlock}`
  * `::BootstrapInput{Stationary}`

## 引数

  * `Input<:DataGenInput`: データを生成するためのパラメータを持つ構造体
  * `nSimulation`: 実行するシミュレーションの数。

## 出力

  * `data`:   nTimeStep x nSimulation 配列で、各列には1つのシミュレーションのデータが含まれ、各行には各タイムステップのデータが含まれます。

## 例

```julia
nTimeStep = 100;
input1 = LogDiffInput(nTimeStep);

# ログ拡散モデルを使用してデータセットを作成
data1 = makedata(input1, 1)

# 定常ブートストラップを使用して2回のシミュレーションを持つ別のデータセットを作成
input2 = BootstrapInput(data1, Stationary; n=100);
data2 = makedata(input2, 2)
```
