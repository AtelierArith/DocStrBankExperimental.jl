```
fourLeafMLE(SITE_PATTERN_DATA)
```

# 説明

モデルの内部およびすべてのサブモデルにわたって局所最大値を計算することにより、ユニークなグローバル最大値を返そうとし、尤度を最大化するもののみのリストを返します。

# 引数

  * `SITE_PATTERN_DATA` : データ内で各サイトパターンが観察される回数を指定する長さ8のサイト頻度ベクトル。パターンは `[xxxx, xxxy, xxyx, xxyy, xyxx, xyxy, xyyx, xyyy]` の順に並んでおり、x と y は異なるヌクレオチドを示します。例えば、ベクトル `SITE_PATTERN_DATA=[14,2,5,10,7,4,3,6]` は、パターン xxxx が14回観察され、パターン xxxy が2回観察され、パターン xxyx が5回観察されることを意味します。

# 出力

尤度を最大化する木（またはサブモデル）に対応するベクトルのリスト。各ベクトルは、次の形式の位置付けられた最大値に対応します。

```

[logL,
 reduced tree class,
 list of compatible binary quartet topologies,
 branch lengths (excluding those which equal 0 or 1),
 branch length names,
 labels,
 verbal description]

```

ここで、「reduced tree class」は、局所最大値を見つけるために必要な計算のタイプによってサブモデルを分類するために著者によって開発されたスキームを指します。非自明なクラスは10個あり（すなわち、一般的なデータに対して非ゼロの尤度を持つもの）、R1, R2, ..., R10 として示されます。例えば、R1 = バイナリクォータ、R2 = スターツリー、R3 から R10 は、`aux-functions-for-R3-through-R10.jl` ファイルのコメントに詳細が記載されている追加のサブモデルタイプを指します。

尤度を最大化する2つ以上の局所最大値が見つかった場合、この関数は複数の最大尤度推定量を返します。これには2つの可能な理由があります（1）MLEが実際にユニークでない、または（2）浮動小数点演算がどの最大値がより大きな尤度を持つかを区別するには不十分に精度が低い。

# 使用例:

```

random_hadamard_edge_parameters=rand(5)
test_model=computeProbabilityVector(random_hadamard_edge_parameters,1)
N=1000
SITE_PATTERN_DATA = rand(Multinomial(N,test_model))
fourLeafMLE(SITE_PATTERN_DATA)
listMaxima(SITE_PATTERN_DATA)

```
