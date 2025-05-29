```
has_kwfn_constructor(def[, name = struct_name_plain(def)])
```

構造体定義に `name` のキーワード関数コンストラクタが含まれているか確認します。デフォルトで確認するコンストラクタ名は、型変数を推論せず、ユーザーがすべての型変数を入力する必要があるプレーンコンストラクタです。詳細は [`struct_name_plain`](@ref) を参照してください。
