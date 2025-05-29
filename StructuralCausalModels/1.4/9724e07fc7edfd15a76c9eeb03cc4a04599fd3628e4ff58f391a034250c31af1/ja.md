# shipley_test

```julia
shipley_test(d)

```

与えられたDAGによって示されるすべての独立性のテスト

サンプル共分散行列に基づいて、与えられた有向非巡回グラフに従って定義されたガウスモデルによって示されるすべての独立性関係の同時テストを計算します。

テスト統計量は C = -2 sum(ln(p*j)) であり、ここで p*j は basiSet(A) によって計算された条件付き独立性のテストのp値です。p値は (0,1) 上の独立した一様変数であり、統計量はちょうど 2k 自由度のカイ二乗分布を持ち、k は基底集合の要素の数です。Shipley (2002) はこのテストをフィッシャーのCテストと呼んでいます。

### メソッド

```julia
shipley_test(;
* `d::Dag`                             : 有向非巡回グラフ
)
```

### 戻り値

```julia
* `res::NamedTuple`                    : (ctest=..., dof=..., pval=...)
```

ここで：

ctest: テスト統計量 C   dof:   自由度。   pval:  テストのP値、両側の代替を仮定。

# 拡張ヘルプ

### 例

### 数学の成績データに対するShipley_test

```julia
using StructuralCausalModels, RData

objs = RData.load(scm_path("..", "data", "marks.rda");
marks_df = objs["marks"]

d = OrderedDict(
  :mechanics => [:vectors, :algebra],
  :vectors => [:algebra],
  :statistics => [:algebra, :analysis],
  :analysis => [:algebra]
);
dag = Dag(d; df=df)
shipley_test(dag)
```

### 参照

```julia
?Dag
?basis_set
?pcor_test
```

### 謝辞

原著者:                       Giovanni M. Marchetti

Juliaへの翻訳:                   Rob J Goedman

### 参考文献

Shipley, B. (2000). A new inferential test for path models based on directed acyclic graphs. Structural Equation Modeling, 7(2), 206–218.

### ライセンス

Rパッケージggmはライセンス: GPL-2の下でライセンスされています。

Juliaの翻訳は: MITの下でライセンスされています。

APIの一部、エクスポートされています。
