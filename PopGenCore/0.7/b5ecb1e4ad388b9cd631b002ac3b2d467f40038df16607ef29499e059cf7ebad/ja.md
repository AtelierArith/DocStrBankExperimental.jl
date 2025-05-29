```
matrix(data::PopData, matrixtype::Union{String, Symbol} = "count", missings = "mean", scale = false, center = false)
```

アレルのカウントまたは頻度の行列を返します。行はサンプル、列はそのサンプルにおけるそのローカスのアレルの出現回数または頻度です。ローカスとアレルはアルファベット順にソートされます。`scale`または`center`を`true`に設定すると、`by`キーワードに関係なくアレルの頻度が計算されます。

### 位置引数

  * `data`: PopDataオブジェクト
  * `matrixtype`: `count`または`frequency`の`String`または`Symbol`（デフォルト: `frequency`）

### キーワード引数

  * `missings`: `frequency`を出力する際に欠損値をどのように扱うかを示す`String`（デフォルト: `mean`）

      * `"missing"`: 欠損値をそのまま保持するフォールバックメソッド
      * `"zero"`: 欠損値を`0`で置き換える
      * `"mean"`: 欠損値をそのローカスにおけるアレルの平均頻度で置き換える
  * `scale`: アレルの頻度をzスコアスケーリングするかどうかの`Bool`（デフォルト: `false`）
  * `center`: アレルの頻度をセンタリングするかどうかの`Bool`（デフォルト: 'false'）

**例**

```
julia> cats = @nancycats ;

julia> cnts = matrix(cats, "count") ;  cnts[1:5,1:6]
5×6 Matrix{Union{Missing, Int8}}:
  missing   missing   missing   missing   missing   missing
  missing   missing   missing   missing   missing   missing
 0         0         0         0         0         0
 0         0         0         0         0         0
 0         0         0         0         0         0

julia> frq = matrix(cats, "frequency") ;  frq[1:5,1:6]
5×6 Matrix{Union{Missing, Float32}}:
 0.00460829  0.00460829  0.0276498  0.133641  0.00460829  0.0921659
 0.00460829  0.00460829  0.0276498  0.133641  0.00460829  0.0921659
 0.0         0.0         0.0        0.0       0.0         0.0
 0.0         0.0         0.0        0.0       0.0         0.0
 0.0         0.0         0.0        0.0       0.0         0.0

 julia> frq = matrix(cats, :frequency, missings = "zero") ;  frq[1:5,1:6]
 5×6 Matrix{Float64}:
 0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0

 julia> frq = matrix(cats, missings = "mean", scale = true, center = true) ;  frq[1:5,1:6]
 5×6 Matrix{Float32}:
  7.17017f-9   7.17017f-9   0.0        0.0        7.17017f-9   0.0
  7.17017f-9   7.17017f-9   0.0        0.0        7.17017f-9   0.0
 -0.0709577   -0.0709577   -0.175857  -0.394198  -0.0709577   -0.300797
 -0.0709577   -0.0709577   -0.175857  -0.394198  -0.0709577   -0.300797
 -0.0709577   -0.0709577   -0.175857  -0.394198  -0.0709577   -0.300797
```

```
