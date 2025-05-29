```
h5merge(output_file::AbstractString, keys_files::Union{AbstractDict{<:AbstractString,<:AbstractString},AbstractVector{<:Pair{<:AbstractString,<:AbstractString}};
      mode::AbstractString="a", skip_existing_entries::Bool=false,
      h5_group_search_depth::Integer=0, h5_strip_group_prefix::Bool=false,
      verbose::Bool=false)
```

複数のファイルを単一のHDF5出力ファイルにマージします。

# 引数

  * `output_file`: データがマージされるHDF5ファイルへのパス。
  * `keys_files`: ターゲットグループ名を入力ファイル名にマッピングするベクターまたは辞書。
  * `mode`: 新しいファイルを作成するための`"w"`または既存のファイルに追加するための`"a"`。
  * `skip_existing_entries`: `true`の場合、出力ファイルに既に存在するグループは上書きされません。
  * `h5_group_search_depth`: 入力HDF5ファイルに対して、グループパスを収集する深さ。

      * `0`はルート（`"/"`）を使用することを意味します。
      * `1`はルートの直下の子を収集することを意味します。
      * より高い値は階層の深いところにあるグループを収集します。
  * `h5_strip_group_prefix`: `true`の場合、ターゲットグループ名（`keys_files`からのキー）は出力HDF5パスから省略されます。例えば、入力ファイルにグループパス`"/level1/level2"`が含まれ、キーが`"parent"`の場合：

      * `h5_strip_group_prefix = false`の場合、出力パスは`"/parent/level1/level2"`になります。
      * `h5_strip_group_prefix = true`の場合、出力パスは`"/level1/level2"`になります。
  * `verbose`: `true`の場合、追加のログ情報が出力されます。

# 挙動

  * `.h5`拡張子の入力ファイルに対して、関数はファイルを開き、`h5_group_search_depth`までのグループパスを収集します。収集された各パスは、フラグ`h5_strip_group_prefix`に従って最初のNコンポーネントを削除することによって修正されます（`true`の場合、親キーは省略されます）。その後、対応するオブジェクトが出力ファイルにコピーされます。
  * その他のファイルタイプ（例：JSON、YAML、テキスト、マークダウン）については、ファイルが読み取られ、テキストまたは生のバイナリデータとして保存されます。
  * 関数は、コピーされた各グループの元のファイルパスを示す属性を記録します。

処理されたグループ名のベクター（文字列として）を返します。
