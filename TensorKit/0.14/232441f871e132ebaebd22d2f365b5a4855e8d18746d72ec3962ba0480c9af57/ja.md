```
tsvd(t::AbstractTensorMap, (leftind, rightind)::Index2Tuple;
    trunc::TruncationScheme = notrunc(), p::Real = 2, alg::Union{SVD, SDD} = SDD())
    -> U, S, V, ϵ
```

(おそらく切り捨てられた)特異値分解を計算します。ここで、`norm(permute(t, (leftind, rightind)) - U * S * V) ≈ ϵ` となり、`ϵ` は切り捨て誤差を表します。

`leftind` と `rightind` が指定されていない場合、`t` の現在の左インデックスと右インデックスのパーティションが使用されます。その場合、`tsvd!(t, trunc = notrunc(), p = 2)` を使用することで、`t` のデータが破壊/上書きされることを許可すれば、より少ないメモリが割り当てられます。

新しい内部次元のために切り捨てパラメータ `trunc` を指定することができ、その場合、切り捨てられた特異値分解が計算されます。選択肢は次の通りです：

  * `notrunc()`: 切り捨てなし（デフォルト）；
  * `truncerr(η::Real)`: 切り捨てられた特異値の p-ノルムが `η` より小さくなるように切り捨てます；
  * `truncdim(χ::Int)`: 内部ベクトル空間の同等の総次元が `χ` より大きくならないように切り捨てます；
  * `truncspace(V)`: 内部ベクトル空間の次元が `V` のいずれかのセクターで小さくなるように切り捨てます；
  * `truncbelow(η::Real)`: すべての特異値が `η` より大きくなるように切り捨てます；

切り捨てオプションは `&` を使用して組み合わせることもでき、つまり `truncbelow(η) & truncdim(χ)` は、すべての特異値が `η` より大きく、内部ベクトル空間の同等の総次元が `χ` より大きくならないように切り捨て空間を選択します。

メソッド `tsvd` は、切り捨てられた特異値の `p` ノルムとして計算された切り捨て誤差 `ϵ` も返します。

キーワード `alg` は、分解を計算する基礎となる LAPACK アルゴリズムに対応する `SVD()` または `SDD()` に等しくすることができます（`_gesvd` または `_gesdd`）。

直交性は `InnerProductStyle(t) <: HasInnerProduct` を必要とし、`tsvd(!)` は現在 `InnerProductStyle(t) === EuclideanInnerProduct()` のみで実装されています。
