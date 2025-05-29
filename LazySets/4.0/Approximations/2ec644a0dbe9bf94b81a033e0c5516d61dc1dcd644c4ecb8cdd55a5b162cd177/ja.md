```
box_approximation(S::CartesianProduct{N, <:AbstractHyperrectangle, <:AbstractHyperrectangle}) where {N}
```

2つのハイパーレクタングル集合の直積をタイトなハイパーレクタングルで過大評価します。

### 入力

  * `S`– 2つのハイパーレクタングル集合の直積

### 出力

ハイパーレクタングル。

### アルゴリズム

このメソッドは`convert`メソッドにフォールバックします。直積配列でラップされた集合はハイパーレクタングルであるため、過大評価なしでこれを行うことができます。
