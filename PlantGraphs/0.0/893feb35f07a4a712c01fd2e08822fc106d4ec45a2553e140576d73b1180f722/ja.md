```
ancestor(c::Context; condition = x -> true, max_level::Int = typemax(Int))
```

ノードの最初の祖先を返します。これは`condition`に一致します。ルールまたはクエリ内で使用することを意図しています。

## 引数

  * `c::Context`: 動的グラフ内のノードに関連付けられたコンテキスト。

## キーワード

  * `condition`: `Context`オブジェクトを入力として受け取り、`true`または`false`を返すユーザー定義関数。
  * `max_level::Int`: アルゴリズムがグラフを横断する際に取ることができる最大ステップ数。

## 詳細

`has_ancestor()`が同じノードと`condition`に対して`false`を返す場合、`ancestor()`は`missing`を返します。それ以外の場合は、一致するノードに関連付けられた`Context`を返します。

## 返り値

`Context`オブジェクトまたは`missing`を返します。

## 例

```jldoctest
julia> struct A1 <: Node val::Int end;

julia> struct B1 <: Node val::Int end;

julia> axiom = A1(1) + (B1(1) + A1(3), B1(4));

julia> g = Graph(axiom = axiom);

julia> function qfun(n)
           na = ancestor(n, condition = x -> (data(x).val == 1))
           if !ismissing(na)
               data(na) isa B1
           else
               false
           end
       end;

julia> Q1 = Query(A1, condition = qfun);

julia> R1 = apply(g, Q1);

julia> Q2 = Query(B1, condition = qfun);

julia> R2 = apply(g, Q2);
```
