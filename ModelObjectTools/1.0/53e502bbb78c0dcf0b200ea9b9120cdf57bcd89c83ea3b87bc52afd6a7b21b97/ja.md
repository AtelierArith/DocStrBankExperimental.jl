vectorRepresentation(input;         fields = fieldnames(typeof(input)))

モデルパラメータまたは平衡変数を表す実数値のベクトルを作成します。このベクトルは、制約なしで最適化に使用できます。すべての要素は、modelObjectToolsVarInfoによって定義された範囲内の値を保持しながら、(-Inf, Inf)の範囲で変化できます。

デフォルトでは、入力構造のすべてのフィールドをエンコードします。フィールドのサブセットのみが必要な場合は、fieldsキーワード引数を設定してください。
