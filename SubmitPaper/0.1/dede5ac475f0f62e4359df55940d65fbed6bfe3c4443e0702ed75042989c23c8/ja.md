```
package(directory; [submission_dir, force_overwrite])
```

`directory`にあるLaTeXプロジェクトを提出用にパッケージ化します。これにより、ルートドキュメントが見つかり、すべての埋め込まれた（`\input`/`\include`を介して）`tex`ファイルが1つのファイルにマージされます。すべての図の参照（`\includegraphics`を介して）を変更し、すべてのネストされたディレクトリを削除してファイル名のみを指すようにします。参照された場所からすべての図を`submission_dir`にコピーし、すべてのネストされたフォルダーを削除します。マージされたファイルを`submission_dir`に書き込みます。その後、新しくマージされたコードを`latexmk`を使用してコンパイルし、その後クリーンアップを行い、`.bbl`ファイルを残します。

## オプションのキーワード引数:

  * `submission_dir`: デフォルトでは`directory/submission`に設定されています。これは提出ファイルがコピーされるフォルダーです。**絶対に**これを`directory`と同じに設定しないでください。
  * `force_overwrite`: 確認なしに`submission_dir`内の既存のすべてのファイルを削除します。
