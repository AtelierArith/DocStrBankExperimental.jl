```julia
getClique(tree, cId)

```

ベイズ（ジャンクション）ツリーにおけるクリクを表すTreeCliqueノードオブジェクトを返します。これは、前面変数`frt<:AbstractString`のいずれかによって定義されます。

ノート

  * 前面変数は、ツリー内のクリクで一度だけ発生するため、ユニークな識別子です。

関連:

getCliq, getTreeAllFrontalSyms
