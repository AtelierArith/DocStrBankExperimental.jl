# 集団を人口サイズで初期化する

```
Cohort(n::Int64=0)
```

### 引数

  * `n` : 人口サイズを割り当てる整数。

### 例

```jldoctest
julia> cohort = Cohort(5)
[ Info: Cohort (5 individuals)
[ Info:
[ Info: 繁殖価の平均:
[ Info: [1.265 1.697]
[ Info:
[ Info: 繁殖価の分散:
[ Info: [1.6 1.4]
```

──────────────────────────────────────────────────────────────

# ジェノタイプ/ハプロタイプファイルで集団を初期化する

```
Cohort(genetic_data ::Union{DataFrame, Array{Int64}}; args...)
Cohort(filename     ::String; args...)
```

### 引数

  * `genetic_data` : 個体とマーカーの次元でジェノタイプ/ハプロタイプを格納する`dataframe`/`2D-array`。
  * `filename` : ジェノタイプ/ハプロタイプデータを格納するファイルへの`filepath`。
  * `n` : ファイルから読み込む行数。デフォルト値は`-1`で、ファイル全体が読み込まれます。
  * `random` : デフォルトでは`true`に設定されており、ファイルから`n`行（個体）をランダムに選択して集団を生成します。
  * `alter_maf` : 提供されたジェノタイプに基づいてMAFを更新する場合は`true`に設定します（デフォルト）。

### `demo_genotypes.csv`と`demo_haplotypes.csv`の例

両方のデモファイルは5つの個体と4つのマーカーの情報を格納しています。デモファイルと対話するには`DATA("demo_genotypes.csv")`を使用します。

```
# demo_genotypes.csv
# 行: 個体、列: マーカー
# ホモ接合体は0と2でコーディングされ、それ以外は1でコーディングされます
2,0,0,1
0,0,1,0
0,1,0,2
1,1,0,2
2,0,2,0

# demo_haplotypes.csv
# 行: 個体、列: アレル
# 参照アレルは0でコーディングされ、それ以外は1でコーディングされます
1,1,0,0,0,0,1,0
0,0,0,0,1,0,0,0
0,0,0,1,0,0,1,1
1,0,1,0,0,0,1,1
1,1,0,0,1,1,0,0
```

### 例

```jldoctest
# ファイル全体を読み込む
julia> cohort = Cohort("demo_haplotypes.csv")
julia> get_genotypes(cohort)
5×4 Array{Int64,2}:
 2  0  0  1
 2  0  2  0
 0  0  1  0
 1  1  0  2
 0  1  0  2

# データフレームで3つの個体をランダムに読み込む。
julia> data = DATA("demo_haplotypes.csv", header=false)
julia> cohort = Cohort(data, random=true, n=3)
julia> get_genotypes(cohort)
3×4 Array{Int64,2}:
 2  0  2  0
 0  1  0  2
 1  1  0  2

# 提供されたファイルでマーカーMAFを置き換える
julia> cohort = Cohort("demo_haplotypes.csv", alter_maf=true)
[ Info: MAFは提供されたハプロタイプ/ジェノタイプに基づいて更新されました
[ Info: Cohort (5 individuals)
[ Info:
[ Info: 繁殖価の平均:
[ Info: [1.418]
[ Info:
[ Info: 繁殖価の分散:
[ Info: [2.012]
```

──────────────────────────────────────────────────────────────

# `Cohort`プロパティを検査する関数:

リストされたすべての関数は、個体のIDを最初の列に挿入するためにキーワード引数`ID=true`を取ることができます。

### ジェノタイプ

`個体`と`マーカー`の次元でのジェノタイプ行列

```jldoctest
julia> get_genotypes(cohort)
5×4 LinearAlgebra.Adjoint{Int64,Array{Int64,2}}:
 0  0  1  0
 2  0  2  0
 2  0  0  1
 0  1  0  2
 1  1  0  2
```

### QTLs

`個体`と`マーカー`の次元でのQTLs行列

```jldoctest
julia> get_QTLs(cohort)
5×3 Array{Int64,2}:
 2  2  0
 0  0  2
 0  1  0
 1  0  2
 2  0  1
```

### 繁殖価

`個体`と`特性`の次元での繁殖価

```jldoctest
julia> get_BVs(cohort)
5×2 LinearAlgebra.Adjoint{Float64,Array{Float64,2}}:
 1.26491   0.0
 3.79473   0.0
 1.26491   1.21268
 0.0       1.69775
 0.632456  1.69775
```

### 系譜

系譜行列、リストされた列は個体のID、父親のID、母親のIDの順です。

```jldoctest
julia> get_pedigree(cohort)
5×3 LinearAlgebra.Adjoint{Int64,Array{Int64,2}}:
1  0  0
2  0  0
3  0  0
4  0  0
5  0  0
```

### マイナーアレル頻度 (MAF)

4つのマーカーのうち3つのQTLがある場合、アレル頻度を比較したいです。

```jldoctest
julia> get_MAF(cohort)
4-element Array{Float64,1}:
 0.5
 0.2
 0.3
 0.5
```

### 表現型

定義された`フェノーム`に基づいて集団の表現型をシミュレートします。`h2`と`ve`はこの一回限りのシミュレーションのために特に割り当てることができます。

```jldoctest
julia> get_phenotypes(cohort)
5×1 Array{Float64,2}:
  1.1126064336992942
 -0.8337021175232547
 -0.363621019381922
  4.042256656472762
  1.7828800511223049
```
