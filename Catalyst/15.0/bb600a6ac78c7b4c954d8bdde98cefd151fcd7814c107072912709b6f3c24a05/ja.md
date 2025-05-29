getmisc(reaction::Reaction)

入力反応の `misc` メタデータフィールドを返します。

引数:

  * `reaction`: `misc` メタデータフィールドを取得したい反応。

例:

```julia
reaction = @reaction k, 0 --> X, [misc="A reaction"]
getmisc(reaction)
```

注意:

  * `misc` フィールドには、任意の有効な Julia 構造体を含めることができます。これは、ここに追加された記号変数を Catalyst がチェックできないことを意味します。これは、ここに保存された記号変数（例：種のパラメータ）が Catalyst にアクセスできないことを意味します。これは、例えば `ReactionSystem` をプログラム的に作成する際に問題を引き起こす可能性があります（この場合、`misc` メタデータフィールドに保存された任意の記号変数も `ReactionSystem` コンストラクタに明示的に提供する必要があります）。
