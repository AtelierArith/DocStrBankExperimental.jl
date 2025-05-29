`db`内のテーブル`name`に対応する`SQLStore.Table`オブジェクトを取得します。

返されるオブジェクトは以下をサポートします：

  * `collect`、`filter`、`first`、`only`を使用して行を`SELECT`。ランダム行選択：`sample`、`rand`。
  * `update!`、`updateonly!`、`updatesome!`を使用して行を`UPDATE`。
  * `delete!`、`deleteonly!`、`deletesome!`を使用して行を`DELETE`。
  * `push!`、`append!`を使用して行を`INSERT`。
  * `schema`、`columnnames`、`ncol`を使用してメタデータを取得。
  * その他：`nrow`、`length`、`count`、`any`。
