```
calckinship(geno::Matrix{Float64})
```

遺伝子型確率配列から親族関係を計算します。

# 引数

  * `geno` は n 人の個体と p のマーカーのための遺伝子型確率行列です。

# 出力

対角線上に 1 が含まれる n x n の対称行列を返します。

___

calckinship(geno::Matrix{Union{Missing,Float64}})

遺伝子型確率配列から親族関係を計算します。

# 引数

  * `geno` は `missing` 値を含む n 人の個体と p のマーカーのための遺伝子型確率行列です。

# 出力

対角線上に 1 が含まれる n x n の対称行列を返します。
