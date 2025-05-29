```
dcc_store(;kwargs...)
```

ストアコンポーネント このコンポーネントを使用して、クライアント側にデータを簡単に保持できます。データはDOMに挿入されません。データはメモリ、localStorage、またはsessionStorageに保存できます。データはIDをキーとして保持されます。

  * `id` (String; 必須): このコンポーネントのIDで、コールバック内でダッシュコンポーネントを識別するために使用されます。IDはアプリ内のすべてのコンポーネントで一意である必要があります。
  * `clear_data` (Bool; オプション): `data_key`に含まれるデータを削除するにはtrueに設定します。
  * `data` (Dict | Array | String | Bool; オプション): IDのために保存されたデータ。
  * `modified_timestamp` (オプション): ストレージが最後に変更された時間。
  * `storage_type` ('local', 'session', 'memory'; オプション): ウェブストレージのタイプ。

memory: メモリ内にのみ保持され、ページをリフレッシュするとリセットされます。local: window.localStorage、ブラウザを終了してもデータは保持されます。session: window.sessionStorage、ブラウザを終了するとデータはクリアされます。
