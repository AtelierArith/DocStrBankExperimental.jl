```
apply_template(target_filename, template::AbstractBinaryTemplate; backup_filename, ensure_zero=true, truncate=false)
```

`AbstractBinaryTemplate`をtarget_filenameに適用し、適切なオフセットにチャンクを書き込みます。

ファイルは`expected_file_size(template)`に拡張されます。

# キーワード

  * `backup_filename` - バックアップテンプレートを保存するファイルの名前。デフォルト: `BinaryTemplates.backup_filename(target_filename)`。
  * `ensure_zero` - 上書きされるバイトが`0x00`でない場合にエラーをスローします。デフォルト: `true`
  * `truncate` - ファイルが予想より大きい場合に切り捨てます。デフォルト: `false`
