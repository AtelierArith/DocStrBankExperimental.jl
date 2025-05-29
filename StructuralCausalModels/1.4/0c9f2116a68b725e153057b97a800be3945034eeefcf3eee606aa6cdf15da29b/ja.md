# pcor

```julia
pcor(d, u)

```

2つの変数間の部分相関を、他の変数のセットが与えられた場合に計算します。

### メソッド

```julia
pcor(;
* `d::DAG`                             : DAGオブジェクト
* `u::Vector{Symbol}`                  : 相関を計算するために使用される変数
)
```

ここで：

u[1], u[2]: 相関を計算するために使用される変数、残りの変数は条件付けセットです。

### 戻り値

```julia
* `res::Float64`                       : u[1]とu[2]の間の相関
```

# 拡張ヘルプ

### 例

### ベクトルと代数の間の相関、分析と統計に条件付け

```julia
using StructuralCausalModels, CSV

df = DataFrame!(CSV.File(scm_path("..", "data", "marks.csv"));
S = cov(Array(df))

u = [2, 3, 4, 5]
pcor(u, S)
u = [:vectors, :algebra, :statistics, :analysis]
```

### 謝辞

原著者:                       Giovanni M. Marchetti

Juliaへの翻訳:                   Rob J Goedman

### ライセンス

Rパッケージggmはライセンス: GPL-2の下でライセンスされています。

Juliaの翻訳はライセンス: MITの下でライセンスされています。

APIの一部であり、エクスポートされていません。
