```
mutable struct Subject <:AbstractSubject
```

サブジェクトはアプリケーションと相互作用するエンティティを表します。

フラットRBACモデルでは、サブジェクトは割り当てられたロールから権限を取得し、直接の割り当てはサポートされていません。

# メソッド

  * grant!
  * revoke!
