```
draw_random_rounds(total_rounds, computation_rounds)
```

計算ラウンドとテストラウンドのランダムなシーケンスを生成します。この関数は、最初に計算ラウンドの数を総ラウンドから計算ラウンドを引くことでテストラウンドの数を計算します。次に、`ComputationRound`と`TestRound`のインスタンスの配列を作成し、これらの配列のシャッフルされた連結を返します。

# 引数

  * `total_rounds`: 総ラウンド数。
  * `computation_rounds`: 計算ラウンドの数。

# 戻り値

  * `Array`: `ComputationRound`と`TestRound`のインスタンスのシャッフルされた配列。

# 例

```julia
total_rounds = 10
computation_rounds = 5
rounds = draw_random_rounds(total_rounds, computation_rounds)
```
