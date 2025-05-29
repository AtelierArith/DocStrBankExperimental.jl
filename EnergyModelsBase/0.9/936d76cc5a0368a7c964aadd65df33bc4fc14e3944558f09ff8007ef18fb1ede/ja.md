```
struct Case <: AbstractCase
```

`EnergyModelsBase`におけるケースを表す型です。モデルへの入力を提供するために以前使用されていた辞書に代わるものです。

# フィールド

  * **`T::TimeStructure`** はモデルの時間構造です。
  * **`products::Vector{<:Resource}`** はモデルに組み込むべきリソースです。

    !!! tip
        `EnergyModelsBase`内のすべての [`ResourceEmit`](@ref) を含む必要がありますが、[`ResourceCarrier`](@ref) を含める必要はありません。ただし、すべてのリソースを含めることが推奨されます。
  * **`elements::Vector{Vector}`** は分析に含めるべき [`AbstractElement`](@ref) のベクトルです。分析が有用であるためには、ノードとリンクのベクトルを少なくとも含む必要があります。
  * **`couplings::Vector{Vector{Function}}`** は個々の関数要素タイプ間のカップリングです。これらの要素は、対応する関数を通じて表されます。例えば、[`get_nodes`](@ref) や [`get_links`](@ref) です。
  * **`misc::Dict`** は、ケース作成のための新しい関数がある場合に、既存の形式で追加の高レベルデータを提供するために利用できる辞書です。これはコンストラクタの適用によって条件付きです。

!!! tip "カップリング"
    `EnergyModelsBase`はリンクとノードのカップリングを必要とします。したがって、デフォルトのアプローチとして、カップリングが指定されていない場合、外部コンストラクタに以下のカップリングを追加します。

    ```julia
    couplings = [[get_nodes, get_links]]
    ```

