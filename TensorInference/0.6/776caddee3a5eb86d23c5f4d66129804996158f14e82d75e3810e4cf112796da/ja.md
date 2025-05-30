```julia
marginals(
    tn::TensorInference.TensorNetworkModel;
    usecuda,
    rescale
) -> Dict{Vector{Int64}}

```

[`TensorNetworkModel`](@ref)内の変数の周辺分布を照会します。この関数は辞書を返し、キーは変数で、値はそれぞれの周辺分布です。周辺分布とは、モデル内の残りの変数を統合または合計することによって得られる、変数のサブセットに対する確率分布です。デフォルトでは、この関数はすべての個々の変数の周辺分布を返します。照会する周辺変数を指定するには、[`TensorNetworkModel`](@ref)を構築する際に`unity_tensors_labels`フィールドを設定します。周辺変数の選択は、テンソルネットワークの収束順序に影響を与えることに注意してください。

### 引数

  * `tn`: 照会する[`TensorNetworkModel`](@ref)。

### キーワード引数

  * `usecuda::Bool`: テンソル収束にCUDAを使用するかどうかを指定します。
  * `rescale::Bool`: 収束中にテンソルを再スケールするかどうかを指定します。

### 例

以下の例は、[`examples/asia-network/main.jl`](https://tensorbfs.github.io/TensorInference.jl/dev/generated/asia-network/main/)から取られています。

```jldoctest; setup = :(using TensorInference, Random; Random.seed!(0))
julia> model = read_model_file(pkgdir(TensorInference, "examples", "asia-network", "model.uai"));

julia> tn = TensorNetworkModel(model; evidence=Dict(1=>0));

julia> marginals(tn)
Dict{Vector{Int64}, Vector{Float64}} with 8 entries:
  [8] => [0.450138, 0.549863]
  [3] => [0.5, 0.5]
  [1] => [1.0]
  [5] => [0.45, 0.55]
  [4] => [0.055, 0.945]
  [6] => [0.10225, 0.89775]
  [7] => [0.145092, 0.854908]
  [2] => [0.05, 0.95]

julia> tn2 = TensorNetworkModel(model; evidence=Dict(1=>0), unity_tensors_labels = [[2, 3], [3, 4]]);

julia> marginals(tn2)
Dict{Vector{Int64}, Matrix{Float64}} with 2 entries:
  [2, 3] => [0.025 0.025; 0.475 0.475]
  [3, 4] => [0.05 0.45; 0.005 0.495]
```

この例では、まず変数1の証拠を0に設定し、その後すべての個々の変数の周辺分布を照会します。返された辞書は、照会された変数に対応するキーを持ち、それらの周辺分布を表す値を持っています。これらの周辺分布はベクトルであり、各エントリは変数が特定の値を取る確率に対応しています。この例では、可能な値は0または1です。証拠変数1の場合、周辺分布は常に[1.0]であり、その値は0に固定されています。

次に、照会する周辺変数として変数2と3、変数3と4をそれぞれ指定します。結合周辺分布は収束時間と空間に影響を与える場合と与えない場合があります。この例では、収束空間の複雑さは2^{2.0}から2^{5.0}に増加し、収束時間の複雑さは2^{5.977}から2^{7.781}に増加します。出力される周辺分布は、照会された変数の結合確率であり、テンソルによって表されます。
