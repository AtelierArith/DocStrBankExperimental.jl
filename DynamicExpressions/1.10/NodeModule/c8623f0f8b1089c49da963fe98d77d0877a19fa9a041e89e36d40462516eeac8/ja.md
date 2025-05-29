```
Node{T} <: AbstractExpressionNode{T}
```

Nodeは、二分木に格納された象徴的な式を定義します。単一の`Node`インスタンスは、この木の1つの「ノード」であり、その子ノードへの参照を持っています。子ノードをたどることで、特定の式を評価したり印刷したりすることができます。

# フィールド

  * `degree::UInt8`: ノードの次数。定数の場合は0、単項演算子の場合は1、二項演算子の場合は2。
  * `constant::Bool`: ノードが定数であるかどうか。
  * `val::T`: ノードの値。`degree==0`で、`constant==true`の場合、これは定数の値です。これは`Node`の全体の型によって指定された型を持ちます（例：`Float64`）。
  * `feature::UInt16`: 特徴ノードの場合に使用する特徴のインデックス。`degree==0`かつ`constant==false`の場合のみ使用されます。`degree == 0 && constant == false`の場合のみ定義されます。
  * `op::UInt8`: `degree==1`の場合、これは`operators.unaops`内の演算子のインデックスです。`degree==2`の場合、これは`operators.binops`内の演算子のインデックスです。言い換えれば、これは演算子の列挙型であり、特定の`OperatorEnum`オブジェクトに依存します。`degree >= 1`の場合のみ定義されます。
  * `l::Node{T}`: ノードの左の子。`degree >= 1`の場合のみ定義されます。親ノードと同じ型です。
  * `r::Node{T}`: ノードの右の子。`degree == 2`の場合のみ定義されます。親ノードと同じ型です。これは二項演算子への右の引数として渡されます。

# コンストラクタ

```
Node([T]; val=nothing, feature=nothing, op=nothing, l=nothing, r=nothing, children=nothing, allocator=default_allocator)
Node{T}(; val=nothing, feature=nothing, op=nothing, l=nothing, r=nothing, children=nothing, allocator=default_allocator)
```

式ツリーに新しいノードを作成します。`T`が型または最初の引数のいずれかで指定されていない場合、渡された`val`の値または`l`および/または`r`から推測されます。これらから推測できない場合、デフォルトで`Float32`になります。

`children`キーワードは、`l`および`r`の代わりに使用でき、子ノードのタプルである必要があります。これは、コンストラクタでスプラッティングを使用できるようにするためです。

`OperatorEnum`を作成することで生成される便利な演算子を介してノードを構築することもできます。

`allocator`キーワード引数で単に`Node{T}()`以外のデフォルトのメモリアロケータを指定することもできます。
