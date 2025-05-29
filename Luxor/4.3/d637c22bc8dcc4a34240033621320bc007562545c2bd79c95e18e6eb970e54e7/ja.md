```
spiral(a, b;
    action = :none,
    stepby = 0.01,
    period = 4pi,
    vertices = false,
    log =false)
spiral(a, b, action;
    stepby = 0.01,
    period = 4pi,
    vertices = false,
    log =false)
```

スパイラルを作成し、現在のパスに追加します。2つの主要なパラメータ `a` と `b` は、開始半径とタイトさを決定します。

線形スパイラル（`log=false`）の場合、`b` の値は次のとおりです：

  * リトゥス: -2
  * 双曲線スパイラル: -1
  * アルキメデスのスパイラル: 1
  * フェルマートのスパイラル: 2

対数スパイラル（`log=true`）の場合：

  * 黄金スパイラル: b = ln(phi) / (pi/2) （約0.30）

0.1周辺の `b` の値は、よりタイトで階段状のスパイラルを生成します。
