ConnectionPool{T}(limit::Int) where T -> GenericPool{T}

`GenericPool{T}`のエイリアスです。

この関数は`GenericPool{T}`のエイリアスであり、便利さのために提供されています。これは、最大同時実行制限`limit`を持つ型`T`のリソースのための新しいリソースプールを作成します。

# 引数

  * `limit::Int`: プールに許可されるリソースの最大数。正の整数でなければなりません。

# 例外

  * `ArgumentError`: `limit`が正の整数でない場合。
