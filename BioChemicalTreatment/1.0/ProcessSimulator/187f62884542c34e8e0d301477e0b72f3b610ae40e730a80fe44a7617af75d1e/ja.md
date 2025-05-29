```
プロセス
```

反応速度を計算し、反応器に提供するために使用される[`AbstractProcessElement`](@ref)の実装。

# コンストラクタ

```
Process(args...; name, error_invalid_composition=true, kwargs...)
```

`BioChemicalReactionSystem`からファイルを読み込んでプロセスを生成し、構成要件が満たされているかをチェックします。

## 引数

  * `args...`: [`Reactions.BioChemicalReactionSystem`](@ref)に渡す引数。可能性についてはそこにあるドキュメントを参照してください。

## キーワード引数

  * `name`: 作成されたシステムの名前
  * `error_invalid_composition`: 無効な構成に対してエラーをスローするかどうか。デフォルトはtrueで、ユーザーに無効な構成が機能することを積極的にアクティブにするよう強制します。この引数が`false`に設定されている場合、エラーの代わりに警告がスローされます。
  * `kwargs...`: モデルのパラメータを指定するキーワード引数。設定するための一致するパラメータが見つからない場合はエラーがスローされます。他のパラメータの値や式である可能性があります。
