GenerateTables(conn; inplace = true, exported = false)

指定されたOMOP CDMデータベース内のすべてのテーブルのJulia表現を生成します。

# 引数:

  * `dialect::Symbol` - SQLクエリに使用されるダイアレクト（利用可能なダイアレクトについては、こちらを参照してください: https://mechanicalrabbit.github.io/FunSQL.jl/stable/reference/#FunSQL.SQLDialect）
  * `schema::String` - 使用されるデータベーススキーマの名前。
