返されるのは、データ型の変換、無効化されたコンポーネントのフィルタリング、グローバルに計算する必要があるシステム全体の値を格納するために、主にデータ辞書からの一般的に使用される事前計算データを格納する辞書です。一般的なキーには以下が含まれます：

  * `:junction` – システム内の接合点のセット、
  * `:pipe` – システム内のパイプのセット、
  * `:pump` – システム内のポンプのセット、
  * `:consumer` – システム内の消費者ポイントのセット、
  * `:producer` – システム内の生産者ポイントのセット、
  * `:tank` – システム内のタンクのセット、
  * `:degree` – 既存の接続を使用している接合点iの次数（`ref_degree!`を参照）。
