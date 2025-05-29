```
build_brkga(problem_instance::AbstractInstance, decode_function!::Function,
            opt_sense::Sense, seed::Int64, chromosome_size::Int64,
            brkga_params::BrkgaParams, evolutionary_mechanism_on::Bool = true,
)::BrkgaData
```

進化的およびパスリリンク手続きで使用される[`BrkgaData`](@ref)オブジェクトを構築します。このデータ構造は`BrkgaMpIpr`関数の外部で変更されるべきではありません。このバージョンはすべての制御引数を受け入れ、調整目的に便利です。

# 引数

  * [`problem_instance::AbstractInstance`](@ref AbstractInstance): 解決すべき問題のインスタンス。
  * `decode_function!::Function`: クロモソームを解にマッピングするために使用されるデコード関数。この関数は次のシグネチャを**持っている必要があります**:

    ```julia
    decode!(chromosome::Array{Float64, 1},
            problem_instance::AbstractInstance,
            rewrite::Bool)::Float64
    ```

    `rewrite == false`の場合、`decode!`は`chromosome`を変更できません。
  * [`opt_sense::Sense`](@ref Sense): 最適化の感覚（最大化または最小化）。
  * `seed::Int64`: 擬似乱数生成器のシード。
  * `chromosome_size::Int64`: 各クロモソームの遺伝子の数。
  * [`brkga_params::BrkgaParams`](@ref BrkgaParams): 設定ファイルから読み込まれたBRKGAおよびIPRパラメータオブジェクト、または手動で作成されたもの。すべてのデータは深くコピーされます。
  * `evolutionary_mechanism_on::Bool = true`: falseの場合、進化は行われず、クロモソームのデコードのみが行われます。各世代で、最良のクロモソームを除くすべての集団が置き換えられます。マルチスタートアルゴリズムをエミュレートするのに非常に便利です。

# 例外

  * `ArgumentError`: 引数またはその組み合わせが無効な場合に発生します。
