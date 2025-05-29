```
initialstates(rnn) -> AbstractVector
```

与えられた再帰セルまたは再帰層の初期隠れ状態を返します。

# 例

```julia
using Flux

# 入力次元10から出力次元20へのRNNCellを作成
rnn = RNNCell(10 => 20)

# 初期隠れ状態を取得
state = initialstates(rnn)

# 入力データを取得
x = rand(Float32, 10)

# 前方に実行
out, state = rnn(x, state)
```
