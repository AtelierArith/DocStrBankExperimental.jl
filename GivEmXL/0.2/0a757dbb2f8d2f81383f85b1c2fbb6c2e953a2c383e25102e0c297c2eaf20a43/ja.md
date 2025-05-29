```
makeproj(tgt_folder, tgt_projname, tgt_scriptname, src::NamedTuple; 
    ignorecase=false, authors::Vector{String}=String[], force=false) → nothing
makeproj(tgt_folder, tgt_projname, tgt_scriptname, src::Symbol; kwargs...)
```

テンプレートプロジェクトをコピーして必要に応じて名前を変更することでプロジェクトを作成します。宛先フォルダーは、ソースの囲むフォルダーとは異なる必要があります。

# 引数

  * `tgt_folder::AbstractString`: 宛先フォルダー
  * `tgt_projname::AbstractString`: 作成するプロジェクトの名前
  * `tgt_scriptname::AbstractString`: 実行可能スクリプトの名前
  * `src::Symbol`: `:default`（デフォルトテンプレート）または `:example1`（おもちゃの例 #1）、または `:example2`（GivEmXLに付属のおもちゃの例 #2）を受け入れます
  * `src::@NamedTuple{src_folder::String, src_scriptname::String}`: 例えば、デフォルトテンプレートの場合は `src=(; src_folder="userproj_template/Template_ProjName", src_scriptname="template_user_scriptname")` となります

# キーワード引数

  * `ignorecase=false`: ファイルパスの大文字と小文字を無視する
  * `authors::Vector{T}=String[] where T <: AbstractString`: プロジェクトの著者（`Project.toml`に記載されます）
  * `force=false`: trueの場合、宛先を上書きします。

関数 `makeproj` は公開されており、エクスポートされていません。
