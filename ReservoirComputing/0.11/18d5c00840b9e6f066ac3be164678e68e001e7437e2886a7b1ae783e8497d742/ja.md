```
modified_lm([rng], [T], dims...;
    factor, amplitude=0.3, sine_divisor=5.9, logistic_parameter=2.35,
    return_sparse=false)
```

ロジスティックマッピングに基づいて入力重み行列を生成します [^viehweg2025]。この行列は、各入力が再帰的なロジスティックマップを介して高次元の特徴空間に変換されるように構築されています。各入力に対して、次のように重みのチェーンが生成されます：

  * チェーンの最初の要素は、サイン関数を使用して初期化されます：

$$
      W[1,j] = \text{amplitude} \cdot \sin( (j \cdot \pi) / 
          (\text{factor} \cdot \text{n} \cdot \text{sine_divisor}) )
$$

ここで `j` は入力に対応するインデックスで、`n` は入力の数です。

  * 続く要素は、ロジスティックマッピングを使用して再帰的に計算されます：

$$
      W[i+1,j] = \text{logistic_parameter} \cdot W[i,j] \cdot (1 - W[i,j])
$$

結果として得られる行列の次元は `(factor * in_size) x in_size` であり、`in_size` は `dims` で提供された列の数に対応します。提供された行の数が `factor * in_size` と一致しない場合、行の数は上書きされます。

# 引数

  * `rng`: 乱数生成器。デフォルトは WeightInitializers の `Utils.default_rng()` です。
  * `T`: リザーバ行列の要素の型。デフォルトは `Float32` です。
  * `dims`: 行列の次元。`res_size x in_size` に従う必要があります。

# キーワード引数

  * `factor`: 各入力ごとのロジスティックマップの反復回数（チェーンの長さ）。各入力ごとの行の数を決定します。
  * `amplitude`: 各ロジスティックチェーンの最初の要素のサインベースの初期化のためのスケーリングパラメータ A。デフォルトは 0.3 です。
  * `sine_divisor`: サイン初期化における位相を調整するために使用されるパラメータ B。デフォルトは 5.9 です。
  * `logistic_parameter`: チェーンの動力学を支配するロジスティック再帰のパラメータ r。デフォルトは 2.35 です。
  * `return_sparse`: `true` の場合、結果の行列をスパース行列として返します。デフォルトは `false` です。

# 例

```jldoctest
julia> modified_lm(20, 10; factor=2)
20×10 SparseArrays.SparseMatrixCSC{Float32, Int64} with 18 stored entries:
⎡⢠⠀⠀⠀⠀⎤
⎢⠀⢣⠀⠀⠀⎥
⎢⠀⠀⢣⠀⠀⎥
⎢⠀⠀⠀⢣⠀⎥
⎣⠀⠀⠀⠀⢣⎦

julia> modified_lm(12, 4; factor=3)
12×4 SparseArrays.SparseMatrixCSC{Float32, Int64} with 9 stored entries:
  ⋅    ⋅          ⋅          ⋅ 
  ⋅    ⋅          ⋅          ⋅ 
  ⋅    ⋅          ⋅          ⋅ 
  ⋅   0.0133075   ⋅          ⋅ 
  ⋅   0.0308564   ⋅          ⋅ 
  ⋅   0.070275    ⋅          ⋅ 
  ⋅    ⋅         0.0265887   ⋅ 
  ⋅    ⋅         0.0608222   ⋅ 
  ⋅    ⋅         0.134239    ⋅ 
  ⋅    ⋅          ⋅         0.0398177
  ⋅    ⋅          ⋅         0.0898457
  ⋅    ⋅          ⋅         0.192168

```

[^viehweg2025]: Viehweg, Johannes, Constanze Poll, and Patrick Mäder. "Deterministic Reservoir Computing for Chaotic Time Series Prediction." arXiv preprint arXiv:2501.15615 (2025).
