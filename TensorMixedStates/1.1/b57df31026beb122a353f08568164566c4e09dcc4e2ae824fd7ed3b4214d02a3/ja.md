```
measure(state, args[, t])
measure(state, measure[, t])
measure(state, [measures...][, t])
```

指定された状態とシミュレーション時間で要求された測定を計算します。

すべての必要な測定を1回の呼び出しで要求する方が効率的です。

# 例

```
measure(state, X(1))     # 可観測量 X(1) を計算
measure(state, X)        # すべてのサイトで可観測量 X を計算
measure(state, (X, Y))   # すべてのサイトのペアで相関 XY を計算
measure(state, Check("check", X(1)X(2), t->sin(2t)), 0.8) # 与えられた可観測量を計算された値と照合してチェック
measure(state, [X(2), Y, (X, Y)]) # 複数の測定を一緒に
```
