```
has_ancestor(c::Context; condition = x -> true, max_level::Int = typemax(Int))
```

ノードが条件に一致する祖先を持っているかどうかを確認します。ルールまたはクエリ内で使用することを意図しています。

## 引数

  * `c::Context`: 動的グラフ内のノードに関連付けられたコンテキスト。

## キーワード

  * `condition`: `Context`オブジェクトを入力として受け取り、`true`または`false`を返すユーザー定義関数。
  * `max_level::Int`: アルゴリズムがグラフを横断する際に取ることができる最大ステップ数。

## 詳細

この関数は、`c`に関連付けられたノードからグラフのルートに向かってグラフを横断し、`condition`が`true`を返すノードが見つかるまで続けます。条件を満たすノードが見つからない場合、`false`を返します。この関数のデフォルト値は、アルゴリズムが常に1ステップ後に`true`を返すように設定されています（ルートノードに適用される場合を除く）。この場合、ノードに対して`has_parent`を呼び出すことと同等です。

アルゴリズムが横断できるレベルの数は`max_level`によって制限されます（主に過剰な計算を避けるためですが、ユーザーは使用しているグラフのトポロジーに基づいて意味のある制限を指定したい場合があります）。

関数`condition`は、`Context`型のオブジェクトを入力として受け取り、`true`または`false`を返す必要があります。

## 戻り値

条件を満たす祖先を持つかどうかを示す`Bool`と、ノードとその祖先を分けるグラフ内のレベル数を示す`Int`の2つの値を持つタプルを返します。

## 例

```jldoctest
julia> struct A1 <: Node val::Int end;

julia> struct B1 <: Node val::Int end;

julia> axiom = A1(2) + (B1(1) + A1(3), B1(4));

julia> g = Graph(axiom = axiom);

julia> function qfun(n)
            has_ancestor(n, condition = x -> data(x).val == 1)[1]
       end;

julia> Q1 = Query(A1, condition = qfun);

julia> R1 = apply(g, Q1);

julia> Q2 = Query(B1, condition = qfun);

julia> R2 = apply(g, Q2);
```
