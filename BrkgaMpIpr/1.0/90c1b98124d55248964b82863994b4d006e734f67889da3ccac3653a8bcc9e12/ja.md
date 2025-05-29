```
build_brkga(problem_instance, decode_function!, opt_sense, seed,
    chromosome_size, configuration_file,
    evolutionary_mechanism_on)::Tuple{BrkgaData, ExternalControlParams}
```

[`BrkgaData`](@ref) オブジェクトを構築し、進化的およびパスリリンク手順で使用します。また、追加の制御パラメータを保持する [`ExternalControlParams`](@ref) を構築します。[`BrkgaData`](@ref) は `BrkgaMpIpr` 関数の外部で変更されるべきではないことに注意してください。このバージョンは、ほとんどのパラメータを構成ファイルから読み取ります。

# 引数

  * [`problem_instance::AbstractInstance`](@ref AbstractInstance): 解決すべき問題のインスタンス。
  * `decode_function!::Function`: クロモソームを解にマッピングするために使用されるデコード関数。この関数は以下のシグネチャを**持っている必要があります**:

    ```julia
    decode!(chromosome::Array{Float64, 1},
            problem_instance::AbstractInstance,
            rewrite::Bool = true)::Float64
    ```

    `rewrite == false` の場合、`decode!` は `chromosome` を変更できません。
  * [`opt_sense::Sense`](@ref Sense): 最適化の感覚（最大化または最小化）。
  * `seed::Int64`: 擬似乱数生成器のシード。
  * `chromosome_size::Int64`: 各クロモソームの遺伝子の数。
  * `configuration_file::String`: BRKGA パラメータを含むテキストファイル。例は <a href="example.conf">example.conf</a> で見つけることができます。"#" の後の内容はコメントと見なされ、無視されます。
  * `evolutionary_mechanism_on::Bool = true`: false の場合、進化は行われず、クロモソームのデコードのみが行われます。各世代で、最良のクロモソームを除くすべての個体群が置き換えられます。マルチスタートアルゴリズムをエミュレートするのに非常に便利です。

# 例外

  * `LoadError`: ファイルが無効な構成ファイルである場合、パラメータが欠落している場合、またはパラメータが不正な形式である場合。
  * `SystemError`: 構成ファイルを開けない場合。
