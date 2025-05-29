```
Rule(nodetype; lhs = x -> true, rhs = x -> nothing, captures = false)
```

`nodetype`型のノードに対する置換ルールを作成します。

## 引数

  * `nodetype`: 一致させるノードの型。

## キーワード

  * `lhs`: `Context`オブジェクトを受け取り、ノードを置き換えるべきかどうかを返す関数または関数のようなオブジェクト（`true`または`false`）。
  * `rhs`: 1つ以上の`Context`オブジェクトを受け取り、置換グラフまたは`nothing`を返す関数または関数のようなオブジェクト。複数の入力を受け取る場合、最初のものは置き換えられるノードに対応します。
  * `captures`: 置換ノードの文脈内でノードをキャプチャするかどうかを示す`false`または`true`。

## 詳細

ルールベースのグラフ書き換えに関する詳細はVPLドキュメントを参照してください。

## 返り値

`Rule`型のオブジェクト。

## 例

```jldoctest
julia> struct A <: Node end;

julia> struct B <: Node end;

julia> axiom = A() + B();

julia> rule = Rule(A, rhs = x -> A() + B());

julia> rules_graph = Graph(axiom = axiom, rules = rule);

julia> rewrite!(rules_graph);
```
