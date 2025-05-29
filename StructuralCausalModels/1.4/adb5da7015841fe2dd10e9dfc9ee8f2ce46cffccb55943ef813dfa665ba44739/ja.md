# m_separation

```julia
m_separation(d, f, s; c, debug)

```

2つのノードのセット間のm_separationを、3番目のセットに条件付けて計算します。

### 必要な引数

```julia
m_separation(
* `d::DAG`                             : DAG
* `f::SymbolList`                      : 最初の頂点またはセット
*  s::SymbolList`                      : 2番目の頂点またはセット
)
```

### キーワード引数

```julia
* `c::SymbolListOrNothing=nothing`     : 条件付けセット
* `debug=false`                        : 実行のトレース
```

### 戻り値

```julia
* `res::Bool`                          : テストのブール結果
```

# 拡張ヘルプ

### 例

### 代数に条件付けた力学と統計の間のm_separation

```julia
using StructuralCausalModels, CSV

df = DataFrame!(CSV.File(scm_path("..", "data", "marks.csv"));

d = OrderedDict(
  :mechanics => [:vectors, :algebra],
  :vectors => [:algebra],
  :analysis => [:algebra],
  :statistics => [:algebra, :analysis]
);

dag = DAG("marks", d, df);
m_separation(marks, [:statistics], [:mechanics]; c=[:algebra]))
```

### 謝辞

原著者:                       Giovanni M. Marchetti

Juliaへの翻訳:                   Rob J Goedman

### ライセンス

Rパッケージggmはライセンス: GPL-2の下でライセンスされています。

Juliaの翻訳はライセンス: MITの下でライセンスされています。

APIの一部、エクスポートされています。
