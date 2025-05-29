```
praff(model::Function, data::Array{Float64, 2}, n::Int; kwargs...)

praff(model::Function, gmodel!::Function, data::Array{Float64, 2},
    n::Int; MAXMS::Int=1, SEEDMS::Int=123456789, batches::Int=1,
    initguess::Vector{Float64}=zeros(Float64, n),
    ε::Float64=1.0e-4, noutliers::Int=-1, ftrusted::Union{Float64,
    Tuple{Float64, Float64}}=0.5)
```

RAFFのマルチコア分散バージョン。主な（必須）引数については[`raff`](@ref)関数の説明を参照してください。すべての通信はチャネルによって行われます。

この関数は、RAFFアルゴリズムを実行するために利用可能な**ローカル**ワーカーをすべて使用します。この関数は*タスク*を使用しないため、すべての並列処理は[Distributed](https://docs.julialang.org/en/latest/manual/parallel-computing/#Multi-Core-or-Distributed-Processing-1)パッケージに基づいています。

オプションの引数は次のとおりです。

  * `MAXMS`: 使用するマルチスタートポイントの数
  * `SEEDMS`: ランダムマルチスタートポイントの整数シード
  * `batches`: 各ワーカーに送信されるバッチのサイズ
  * `initguess`: マルチスタート手順で使用される開始点
  * `ε`: 停止許容誤差
  * `noutliers`: 予想される外れ値の最大数を示す整数。デフォルトは*半分*です。*非推奨*。
  * `ftrusted`: 信頼できるポイントの最小予想割合を示す浮動小数点数。デフォルトは*半分*（0.5）です。信頼できるポイントの割合を示す形式のタプル`(fmin, fmax)`でも指定できます。

解を含む[`RAFFOutput`](@ref)オブジェクトを返します。
