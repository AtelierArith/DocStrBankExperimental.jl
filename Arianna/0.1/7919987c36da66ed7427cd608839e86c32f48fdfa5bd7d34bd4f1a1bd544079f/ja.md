```
StoreParameters(chains; dependencies=missing, path=missing, ids=missing, store_first=true, store_last=false, extras...)
```

新しい StoreParameters インスタンスを作成します。

# 引数

  * `chains`: パラメータを保存するチェーンのベクター
  * `dependencies`: パラメータストアの依存関係
  * `path`: パラメータファイルへのパス
  * `ids`: 保存するパラメータの ID
  * `store_first`: 最初のステップでパラメータを保存するフラグ
  * `store_last`: 最後のステップでパラメータを保存するフラグ
  * `extras`: 追加のキーワード引数

# 戻り値

  * `algorithm`: StoreParameters インスタンス
