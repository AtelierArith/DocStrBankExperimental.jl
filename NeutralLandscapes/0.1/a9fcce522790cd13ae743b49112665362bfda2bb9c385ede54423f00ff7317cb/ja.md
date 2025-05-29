```
PerlinNoise <: NeutralLandscapeMaker

PerlinNoise(; kw...)
PerlinNoise(periods, [octaves=1, lacunarity=2, persistance=0.5, valley=:u])
```

0-1の範囲の値を持つパーリンノイズ中立風景モデルを作成します。

# キーワード

  * `periods::Tuple{Int,Int}=(1,1)`: 最初のオクターブの行と列の次元にわたるパーリンノイズの周期の数。
  * `octaves::Int=1`: パーリンノイズを形成するオクターブの数。
  * `lacunarity::Int=2` : 各オクターブの周期の周波数が増加する割合。
  * `persistance::Float64=0.5` : 各オクターブの振幅が減少する割合。
  * `valley::Symbol=`:u`: 模倣される谷底の種類:`:u`はu字型の谷を生成し、`:v`はv字型の谷を生成し、`:-`は平坦な底の谷を生成します。

注意: これは一部の設定でメモリを多く消費するアルゴリズムです。大きな配列サイズ、高いラクリナリティ、および/または多くのオクターブを使用する場合は、`period`に大きな素数を使用する際に注意してください。メモリ使用量は`periods`の最小公倍数に比例します。
