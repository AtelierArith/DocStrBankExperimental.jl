**次の結果ページを取得する**

この関数は次の結果ページを取得します。デフォルトでは、クエリを20ずつ処理します。これは、`.query["limit"]`の値を300までの任意の値に変更することで修正できます。これは、GBIFがクエリに設定した制限です。

このクエリに以前にフィルターが適用されている場合、それらは*削除*され、以前の発生と新しい発生が同じステータスを持つことが保証されますが、すでに取得されたレコードに対してのみ適用されます。
