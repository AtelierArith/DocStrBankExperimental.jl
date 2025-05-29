```
vertices_list(em::ExponentialMap; [backend]=get_exponential_backend())
```

ポリトピック指数写像の頂点のリストを返します。

### 入力

  * `em`      – ポリトピック指数写像
  * `backend` – （オプション; デフォルト: `get_exponential_backend()`）指数化バックエンド

### 出力

頂点のリスト。

### アルゴリズム

基になる集合 `X` がポリトピックであると仮定します。すると、結果は `X` の頂点に適用された指数写像に過ぎません。
