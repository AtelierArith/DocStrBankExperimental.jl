`ident`は、コンテキストとキーワードとして供給された一部のデータから`Ident`を作成します。

キーワード引数:

  * `tag::Union{ScopeTag, Nothing}`。`Ident`が存在するスコープのタグ。
  * `name::Union{Symbol, Nothing}`。識別子の名前。
  * `lid::Union{LID, Nothing}`。スコープ内の識別子のlid。
  * `level::Union{Int, Nothing}`。コンテキスト内のスコープのレベル。
  * `strict::Bool`。`strict`がtrueの場合、見つからなければエラーを投げ、そうでなければ何も返さない。
