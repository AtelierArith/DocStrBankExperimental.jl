`Coset(G::Group,phi=one(G))` は、`G` が `Group{<:T}` であり、`phi` が `T` であるときに、（左）コセット `G.phi` を `Cosetof{T}` 型のオブジェクトとして構築します。この一般的なコセットは、このモジュールで定義されたコセット `C=G.phi` に対する一般的なメソッドのみを知っています。これらは次の通りです。

  * `Group(C)` は `G` を返します。
  * `isone(C)` は `true` を返します。もし `phi in G` であれば。
  * `one(C)` は自明なコセット `G.1` を返します。
  * `length(C)` は `length(G)` を返します。
  * `elements(C)` は `elements(G).*Ref(phi)` を返します。
  * `x in C` は `x/phi in G` を返します。
