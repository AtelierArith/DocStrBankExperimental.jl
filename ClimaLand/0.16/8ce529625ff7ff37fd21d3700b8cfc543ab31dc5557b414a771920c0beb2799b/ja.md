```
make_set_initial_cache(model::AbstractModel)
```

set*initial*cache! 関数を返し、これは補助状態 `p` を Y(t=t0) = Y0 に対応する初期値でインプレースで更新します。

原則として、この関数は必要ありません。なぜなら、t=t0 のときに `explicit_tendency` または `implicit_tendency` のいずれかを最初に評価する際に、Y=Y0 の初期条件を使用して補助状態が更新されるからです。しかし、シミュレーションを実行する前に初期の `p` 状態を設定しないと、t=t0 で保存された出力の `p` の値は未設定のままになります。

さらに、この関数の特定のメソッドは、補助状態に時間に依存しない空間的に変化するパラメータフィールドを格納するモデルにとって有用かもしれません。この場合、`update_aux!` は何もする必要はありませんが、シミュレーションを実行する前に初期（定数）値で設定する必要があります。
