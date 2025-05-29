```julia
struct MechanismState{X, M, C, JointCollection}
```

`MechanismState`は、全体の`Mechanism`の状態情報を格納します。これは、関節の構成と速度ベクトル$q$と$v$、および追加の状態ベクトル$s$を含みます。さらに、$q$と$v$に依存するキャッシュ変数を格納し、二重作業を防ぐことを目的としています。

型パラメータ:

  * `X`: $q$、$v$、および$s$ベクトルのスカラー型。
  * `M`: `Mechanism`のスカラー型
  * `C`: キャッシュ変数のスカラー型（`== promote_type(X, M)`）
  * `JointCollection`: `treejoints`および`nontreejoints`メンバーの型（`TypeSortedCollection`のサブタイプ）
