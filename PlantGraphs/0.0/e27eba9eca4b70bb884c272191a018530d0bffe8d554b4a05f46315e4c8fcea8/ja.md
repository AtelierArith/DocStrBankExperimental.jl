```
Query(N::DataType; condition = x -> true)
```

`nodetype`のタイプのノードと`condition`に一致するクエリを作成します。

## 引数

  * `N::DataType`: 一致させるノードのタイプ。

## キーワード

  * `condition`: ノードが選択されるべきかをチェックする関数または関数のようなオブジェクト。

## 詳細

`nodetype`は具体的なタイプを指し、グラフ内に格納されているタイプのいずれかに一致する必要があります。抽象タイプやグラフに含まれていないタイプは許可されますが、クエリは決して何も返しません。

`condition`は`Context`を入力として受け取り、`true`または`false`を返す関数または関数のようなオブジェクトでなければなりません。デフォルトの`condition`は常に`true`を返すため、クエリは

## 戻り値

`Query`タイプのオブジェクトを返します。動的グラフでクエリを実行するには`apply()`を使用します。

# 例

```jldoctest
julia> struct A <: Node end;

julia> struct B <: Node end;

julia> axiom = A() + B();

julia> g = Graph(axiom = axiom);

julia> query = Query(A);

julia> apply(g, query);
```
