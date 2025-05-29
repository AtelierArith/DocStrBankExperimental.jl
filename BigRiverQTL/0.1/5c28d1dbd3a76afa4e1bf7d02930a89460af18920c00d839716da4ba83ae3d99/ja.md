```
encode_genotype(geno_dict::Dict{String, Any}, geno_val::AbstractArray) -> Matrix
```

事前に定義されたマッピングの辞書を使用して、遺伝子型値の行列をエンコードします。

# 引数

  * `geno_dict::Dict{String, Any}`: 遺伝子型文字列を整数コードにマッピングする辞書。
  * `geno_val::AbstractArray`: エンコードされる遺伝子型文字列の配列。

# 戻り値

  * `Matrix{Union{Missing, Int64}}` または `Matrix{Int64}`: `geno_val` と同じ次元の行列で、各遺伝子型文字列が対応する整数コードに置き換えられます。 `geno_dict` に見つからない遺伝子型は `missing` としてエンコードされます。

# 説明

この関数は、元の `geno_dict` を保持するために提供された辞書を最初にコピーします。次に、辞書にすでに存在しない `geno_val` の遺伝子型を特定します。これらの欠落している遺伝子型について警告が発行され、`missing` へのマッピングで辞書に追加されます。

入力 `geno_val` の各要素は、`geno_dict` からの対応する整数コードによって `encoded_val` 行列内で置き換えられ、既存の遺伝子型マッピングと新たに追加されたマッピングの両方を処理します。

# 例

```julia
geno_dict = Dict{String, Any}("AA" => 1, "AB" => 2, "BB" => 3)
geno_val = ["AA", "AB", "BB", "BC"]
encoded_matrix = encode_genotype(geno_dict, geno_val)
println(encoded_matrix)
```
