```
Node(id::UInt, labels::Vector{String}, properties::Config) <: AbstractNodeLike
```

プロパティグラフのノードを表します。

# フィールド

  * `id::UInt`: ノードの一意の識別子。
  * `labels::Vector{String}`: ノードに関連付けられたラベルのベクター。ラベルはノードをグループ化または分類するために使用されます。
  * `properties::Config`: ノードに関連付けられたプロパティ（キーと値のペア）を表す`Config`オブジェクト。

# コンストラクタ

  * `Node(id::UInt, labels::AbstractString...; props...)`: 指定された`id`、1つ以上の`labels`、および`Config`コンストラクタに渡されるオプションの`props`を使用して`Node`を作成するための便利なコンストラクタ。

# 例

```julia
Node(1, :person, :human, name="John Doe", age=25)
```
