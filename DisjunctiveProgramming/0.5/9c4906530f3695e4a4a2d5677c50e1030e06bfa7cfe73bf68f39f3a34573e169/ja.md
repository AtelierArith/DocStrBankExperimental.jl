```
@disjunction(model, expr, kw_args...)
```

式 `expr` で記述された選言を追加します。`expr` は `LogicalVariableRef` の `Vector` でなければなりません。

```
@disjunction(model, ref[i=..., j=..., ...], expr, kw_args...)
```

式 `expr` で記述された選言のグループを追加します。これは `i`、`j`、... によってパラメータ化され、`LogicalVariableRef` の `Vector` でなければなりません。

上記の両方の呼び出しでは、[`Disjunct`](@ref) タグを追加してネストされた選言を作成できます。

`kw_args` で認識されるキーワード引数は以下の通りです：

  * `base_name`: 制約名を生成するために使用される名前プレフィックスを設定します。スカラー制約の制約名に対応し、そうでない場合は、軸 `axes` の各インデックス `...` に対して制約名が `base_name[...]` に設定されます。
  * `container`: コンテナタイプを指定します。
  * `exactly1`: 選言の中で1つの選択肢のみを許可する制約を追加するかどうかを示す `Bool` を指定します。

マクロを使用せずに選言を作成するには、[`disjunction`](@ref) を参照してください。
