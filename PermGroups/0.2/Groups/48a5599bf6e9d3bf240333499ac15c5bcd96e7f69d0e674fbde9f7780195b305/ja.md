`NormalCoset(G::Group,phi=one(G))` は、`C=G.phi` というコセットを構築します。ここで、`G` は `Group{<:T}` であり、`phi` は `T` 型です。`phi` が `G` を正規化することが前提とされています。この一般的なコセットは、モジュール `Groups` で定義された正規コセットに対する一般的なメソッドのみを知っています。これには、コセットに対して定義されたメソッド（`Coset` を参照）に加えて、以下のメソッドが含まれます。

  * `inv(C)` は `G.inv(phi)` を返します（`inv(phi).G` と等しいと仮定されています）
  * `C*D` は、別のコセット `G.psi` が与えられた場合、`G.phi*psi` を返します
  * `C/D` は、別のコセット `G.psi` が与えられた場合、`G.phi*inv(psi)` を返します
  * `C^D` は、別のコセット `G.psi` が与えられた場合、`G.inv(psi)*phi*psi` を返します
  * `C^n` は `G.phi^n` を返します
  * `order(C)` は、`isone(C^n)` となる最小の `n` を返します

正規コセット `G.phi` の共役類は、`G` が `G.phi` に対して行う共役作用に関連しています。関数 `conjugacy_classes, nconjugacy_classes, classreps, position_class` があります。

最後に、2つのグループに対する関数 `G/H` は、`NormalCoset` の群として商を構築し、`fusion_conjugacy_classes(H::NormalCoset,G::NormalCoset)` は共役類の融合を表現します。
